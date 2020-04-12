# 2020华为软件精英挑战赛

由于平台太迷弃坑。

问题：给一个有向图，问有多少个长度在3-7的简单环。

# 思路
ID离散化。

深搜找出距离每个点正走3步以内的点和倒走3步以内的点。枚举一条边(x, y)，满足x < y则枚举
$$(b_x(1), f_y(1)), (b_x(1), f_y(2)),(b_x(1), f_y(3)),(b_x(2), f_y(3)),(b_x(3), f_y(3))$$
中相同的点z。其中$b_a(k)$为a为起点反走有向边k步，$f_a(k)$为a为起点正走有向边k步。找出所有(z -> x), (y -> z)的路径，乘法原理组合，同时检查是否满足x为全环最小，环为简单环。如果是，加入结果集合。

结果集合排序输出。

# 可优化点
- listf可以只保留比当前点大的
- getroute可以提前删去包含过小点的情况，减少枚举
- listf, listr相关的dfs3, getroute思路优化
- checksame时，(0,2)(1,1)(2,0)之类的等价，可以选少的check
- 枚举边按照从小到大，可以省了最后的排序
- dfs可以换成bfs减少重复
- 枚举边找环和dfs可以多线程
- STL代码的优化
- 输入输出优化
- 离散化代码优化
