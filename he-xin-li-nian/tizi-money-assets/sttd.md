# stTD

用户把TD质押可以获得stTD，质押后的TD进入质押池。

TD与USDC保持1:1的挂钩比例，当USDC参与各种策略获得收益，质押池中的TD会随之增加。

项目的净现值计算包括三个部分：主钱包中尚未分发的USDC、项目在多条链上的跨链USDC，以及通过不同策略收集并由其他代币兑换的USDC。

$$
NPV=USDC_m+USDC_p+USDC_c
$$

如果净现值大于当前总资产netAssets，则产生资产正增长，向质押池中铸造NPV-netAssets数量的TD，增长的数量会在接下来7天中线性释放；如果净现值小于当前总资产netAssets，则资产负增长，在质押池中销毁netAssets-NPV数量的TD。随后将netAssets设置为净现值。

随着质押池中的TD增加，stTD和TD的兑换比例会随时间增长。比例遵循ERC4626标准的设计，如公式（2）（3）所示，其中totalShares是stTD的数量，totalAssets是质押池中已释放的TD的数量。

$$
Assets = Shares * (totalAssets / totalShares)
$$

$$
Shares = Assets * (totalShares / totalAssets)
$$

将stTD解除质押需要等待7天，之后可以兑换成TD。

stTD功能和TD一样，都可以跨链使用。
