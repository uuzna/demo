<script src="https://cdn.jsdelivr.net/npm/mermaid/dist/mermaid.min.js"></script>
<script>mermaid.initialize({startOnLoad:true});</script>
# demo
usecase 用户 {
  "发起退款申请" --> (等待卖家处理)
  (等待卖家处理) --> 卖家
  卖家 --> |同意退款| 系统 : 处理退款
  系统 --> 买家 : 返还退款金额
  卖家 --> |拒绝退款| 系统 : 记录拒绝原因
  用户 --> |无法达成一致| 客服 : 申请介入处理
  客服 --> |审核申请| 系统
  系统 --> 客服 : 处理申请
}

usecase 系统 {
  "记录退款记录" --> (查询退款记录)
  (查询退款记录) --> 用户
  "统计退款金额" --> (生成报表)
  (生成报表) --> 管理员
  "优化退款流程" --> (分析数据)
  (分析数据) --> 管理员
}

usergroup 用户组
usergroup 管理员

用户组 --> 用户
管理员 --> 系统
