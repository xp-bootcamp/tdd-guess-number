# TDD @Guess Number

![Build](https://github.com/xpbootcamp/tdd-guess-number/workflows/Build/badge.svg)
本项目代码采用了采用tdd的方式实现猜数字游戏

## 开发环境
 - JDK1.8+

## 学习目标
- 熟悉 IntelliJ IDEA 快捷键；
- 掌握 TDD 基本知识；
- 识别代码坏味道，熟练运用重构手法；
- 使用 JUnit、AssertJ 与 Mockito 测试框架；


## 业务需求
1. 游戏有四个格子，每个格子有一个0到9的数字，四个格子的数据不能有重复，四个格子的数字组合成为目标答案，比如`1 2 3 4`。
2. 你有6次猜答案的机会，任意一次猜对了则获胜，否则失败。
3. 猜测时需依序输入4个不重复的数字，程序会根据给出答案，答案格式是`xBxS`，B前面的数字代表位置和数字都对的个数，S前面的数字代表数字对但是位置不对的个数。

例如：目标答案是`1 2 3 4`， 那么对于不同的输入，有如下的输出：

|输入  |	输出	|  说明  |
| ---- | :----: | ---- |
|6 7 8 9 | 0B0S	|都不对|
|6 7 8 2 | 0B1S	|2位置不对|
|6 7 1 2 | 0B2S	|1,2位置不对|
|6 3 1 2 | 0B3S	|1,2,3位置不对|
|4 3 2 1 | 0B4S	|1,2,3,4位置都不对|
|1 5 8 9 | 1B0S	|1位置正确|
|1 5 2 7 | 1B1S	|1位置正确，2位置不正确|
|1 5 2 3 | 1B2S	|1位置正确，2，3位置不正确|
|1 4 2 3 | 1B3S	|1位置正确，2，3，4位置不正确|
|1 2 5 0 | 2B0S	|1,2位置正确|
|1 2 5 3 | 2B1S	|1,2位置正确，3位置不正确|
|1 2 4 3 | 2B2S	|1,2位置正确，3,4位置不正确|
|1 2 3 0 | 3B0S	|1,2,3位置正确|
|1 2 3 4 | 4B0S	|全中，胜出 |
|1 2	| Error	| 输入不正确，重新输入 |
|1 1 2 3 | Error	| 输入不正确，重新输入 |
|1 1 2 10 | Error | 输入不正确，重新输入 |

答案在游戏开始时随机生成。你只有6次输入的机会，每次程序应给出当前猜测的结果，以及之前所有猜测的数字和结果以供玩家参考。输入界面为控制台（Console），以避免太多与问题无关的界面代码。输入时，用空格分隔数字
