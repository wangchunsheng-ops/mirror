1. # Terminology Explanation

|      | Terminology | Description |
| :--- | :---------- | :---------- |
| 1    |             |             |
| 2    |             |             |
| 3    |             |             |

1. # Background

Given that the original card content of FEP2PP is no longer relevant, it needs to be removed. Additionally, some new items need to be added.

1. # Solution

1. ## 修改前卡片消息内容

| 序号       | 标题                                                | 参数                                                         | 含义                                                         | 备注                                                         |
| :--------- | :-------------------------------------------------- | :----------------------------------------------------------- | :----------------------------------------------------------- | :----------------------------------------------------------- |
| 1          | L1 & L2 GasPrice                                    | Log Time                                                     | 监控参数的查询时间                                           |                                                              |
| 2          | Pending Tx Count                                    | pending的交易数                                              | 观察待处理交易数                                             |                                                              |
| 3          | L1 GasPrice                                         | L1 （ETH主网）的GP                                           |                                                              |                                                              |
| 4          | L2 GasPrice                                         | L2（X Layer主网）的GP                                        |                                                              |                                                              |
| 5          | **L1 Account Status****（将删除）**                 | Sequencer EOA                                                | L1上sequencer账户的ETH余额                                   | Seq EOA和L1上的zkevm合约交互，观察seq EOA的ETH余额是否足够，是否需要充值 |
| 6          | Sequencer POL                                       | L1上sequencer账户的POL的余额                                 | Seq EOA在提交batch时向合约发送POL代币，完成证明验证后合约会返还该部分POL |                                                              |
| 7          | Aggregator Total                                    | L1上aggregator账户（不由我们控制）提交VerifyBatch的总ETH花费 | agg中Polygon针对networkid=3的提交的花费，从第1个Batch（高度19548763）到最新Batch的总花费 |                                                              |
| 8          | **Profitability****（观察盈利情况）****（将删除）** | Total ETH Used                                               | Seq EOA和agg EOA花费的ETH总量                                |                                                              |
| 9          | Total OKB Gain                                      | 收到的L2用户发送交易支付的gas费总量                          | coinbase地址的余额，可观察OKB收益                            |                                                              |
| 10         | Daily ETH Used                                      | 每日Seq EOA和agg EOA花费的ETH量                              | 统计时间从昨日早上8点到今日早上8点                           |                                                              |
| 11         | Daily OKB Gain                                      | 每日收到的L2用户发送交易支付的gas费                          | 统计时间从昨日早上8点到今日早上8点                           |                                                              |
| 12         | L2 Block Number & Batch Number                      | eth_blockNumber                                              | 当前最新的高度                                               |                                                              |
| 13         | Batch Accepted on L2                                | 完成打包的batch数Accepted on L2                              |                                                              |                                                              |
| 14         | **Historical Max Batch Interval****(将删除)**       | Max BA-BR                                                    |                                                              |                                                              |
| Max BR-BV1 |                                                     |                                                              |                                                              |                                                              |

1. ## 修改后卡片内容

| 序号 | 标题                           | 参数                            | 含义                        | 备注 |
| :--- | :----------------------------- | :------------------------------ | :-------------------------- | :--- |
| 1    | L1 & L2 GasPrice               | Log Time                        | 监控参数的查询时间          |      |
| 2    | Pending Tx Count               | pending的交易数                 | 观察待处理交易数            |      |
| 3    | L1 GasPrice                    | L1 （ETH主网）的GP              |                             |      |
| 4    | L2 GasPrice                    | L2（X Layer主网）的GP           |                             |      |
| 12   | L2 Block Number & Batch Number | blockNumber(latest)             | 当前最新的高度              |      |
| 13   | Batch Accepted on L2           | 完成打包的batch数Accepted on L2 |                             |      |
| 14   | blockNumber(finalized)         | 最终确认区块                    |                             |      |
| 15   | Supply                         | OKB                             | total OKB amount On X Layer |      |
| USDT | Add USDT amount On X Layer     |                                 |                             |      |
| USDC | Add USDC amount On X Layer     |                                 |                             |      |
| 16   | Latest Settled Certificate     | HASH                            | TIME                        |      |

1. ##  原型图对比

![img](https://okg-block.sg.larksuite.com/space/api/box/stream/download/asynccode/?code=NGZmYjljN2ZmMmMzYWVkOWFjNGY1OWQ0YmU3N2JjNWVfbWpYUUIxVFBXaTd0ekRna1BHZmlWSTNYaDU4Q0swcVFfVG9rZW46VHZVaWJlenA0bzVnOFV4MFZvVGx0cFdxZ2FjXzE3NTQwMzg5MTM6MTc1NDA0MjUxM19WNA)![img](https://okg-block.sg.larksuite.com/space/api/box/stream/download/asynccode/?code=NzUyM2QyNDBjYjk3Y2Y2MzQ0YTQxY2M0OWEyYmNmMDlfYmpqSFl2QURNYmRQQzhaVGVhR0Z3QU5tOUg3RjJjQ1BfVG9rZW46TU1xNmJVcjZnb0VUVFF4QWRBSmwxQWdlZ29lXzE3NTQwMzg5MTM6MTc1NDA0MjUxM19WNA)

原卡片

新卡片





会议纪要：

- 讨论当前X Layer升级为pp后，card-robot需要删除和新增的字段。

决定和TODO:

- 决定删除**L1 Account Status**，**Profitability**，**Historical Max Batch Interval**两个模块。
- 决定删除L2 Block Number & Batch Number模块下除最新区块和完成打包的batch数的所有字段，添加最终确认区块。
- 新增Supply，Latest Settled Certificate模块。
- 按照上述约定，修改card-robot机器人消息。