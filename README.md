# IMDMOEA CODE

## 一、算法的总体流程

![](https://github.com/xtuxky/IMDMOEA/blob/master/IMDMOEA_flow.png)

## 二、算法中各个函数接口的说明

| 函数名           | 函数功能                                                     | 入参                                                         | 出参                                                         |
| :--------------- | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| gradient_predict | 在决策空间对种群进行聚类预测，<br>并以向量形式输出种群下一时刻可能的进化方向及进化步长 | Pt1: t-1时刻的种群<br>Pt2: t 时刻的种群<br>Global: 包含变化严重程度和频率信息<br>center:连续时刻的聚类中心点位置<br>seq:聚类中心点的迭代序号<br>idx:种群中个体的归属类 | Population_cluster:种群的聚类结果<br>center:聚类中心点信息（包含进化向量）<br>P1:预测的下一时刻种群 |

| 函数名      | 函数功能                 | 入参                                                         | 出参                                          |
| ----------- | ------------------------ | ------------------------------------------------------------ | --------------------------------------------- |
| PS_Sampling | 在决策空间中生成探索种群 | Pt2:t时刻的种群<br>sample:对每个个体的采样数目<br>seq:聚类中心点的迭代序号<br>center:聚类中心信息（包含进化向量）<br>Population_cluster:种群的聚类结果<br>Global:变化频率等基础信息 | P2:生成的探索种群<br>history_pop:P2的副本信息 |

| 函数名      | 函数功能                                                     | 入参                                                         | 出参                  |
| ----------- | ------------------------------------------------------------ | ------------------------------------------------------------ | --------------------- |
| PF_Sampling | 用于预测下一时刻POF可能出现的区域，并选择探索种群中的优秀个体进行高斯变异 | Pt1:t-1时刻的种群<br>Pt2:t时刻的种群<br>history_pop:探索种群<br>acc:POF的预测精度<br>Global:环境变化的基础细腻系 | P3:诱导变异生成的种群 |

| 函数名            | 函数功能                               | 入参                            | 出参                         |
| ----------------- | -------------------------------------- | ------------------------------- | ---------------------------- |
| CrowdingDistance1 | 在决策空间中计算种群中个体的拥挤度距离 | PopObj:决策空间种群中个体的坐标 | CrowDis:每个个体的拥挤度距离 |
