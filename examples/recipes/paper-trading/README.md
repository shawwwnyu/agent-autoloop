# 接入 A 股模拟交易项目

完整业务已拆分到 [shawwwnyu/a-share-paper-trading](https://github.com/shawwwnyu/a-share-paper-trading)，包括行情、模拟成交、账本、复盘、策略验证与测试。

中台负责定时触发、分发、重派和卡片回答。本目录保留接入指引。

1. 克隆独立项目，按其 README 配置并初始化模拟账户。
2. 将交易项目 integrations/agent-autoloop/rules.json 合入中台规则，修改 worker、cwd 和账户配置路径。
3. 运行 agent-autoloop check，再按现有流程加载规则。

[完整接入与旧账户迁移说明](https://github.com/shawwwnyu/a-share-paper-trading/blob/main/integrations/agent-autoloop/README.md)

两边通过现有 command、轮次资料和 JSON 回执协议连接。交易数据库、行情来源、成交规则和策略版本由交易项目维护，中台保持通用。

中台源码中原有的 cli.ts 入口已迁到独立项目 src/cli.ts。已启用原模板时先暂停相关规则、等待命令退出并备份账户，再按迁移说明更新路径。
