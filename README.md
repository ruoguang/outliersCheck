# OutliersCheck 异常值检查，检出，融合结果
# Simple description 
就是对一组数据进行规则检查，找出并去除异常结果，得到最后融合结果。
# e.g:
下面同一室内同一地点同一时间段采集到一组温度数据，可能存在异常的是？

  温度（℃）： 23,26,26,23,32,22,23,23;
  
那么肉眼观察这个5号采集点可能发生异常，可以通过本算法可以找出5号可能发生异常，该32度就在统计时可以统计，去除掉之后返回剩下7个值的集合。
# Quick start
下载和导入依赖后，使用工具类CCUtil即可。

这里提供了一个简单有效的全自动方法autoOcMap(List list)的方法，只要传入一个集合，就能返回异常值的下标和异常值的map集合。
如果你只想要最后的融合结果（去除异常值的集合），这里提供了autoFusionList(List list)，返回的就是已经剔除异常值的集合，这个是常用方法。
还有的情况下我们只想对最终平均值的拿取，比如上面实例中，真正有意义的就是去掉32度剩下的7个平均值才是有意义的温度采集，
这里提供了一个fusionValue(List list) 获得就是融合平均值。
# Algorithm principle 
基于3σ准则改进的可自动化实现数据校验算法。简单而言，就是符合正太分布的数据，我们都可以用这个算法来实现超大数据量的异常值剔除和融合。
# Explain
由于本人的小白水平，暂且只是大致方向上的概述和简单实现，中间代码，逻辑，数据量，优化等等还有许许多多的不足之处，比如：

1.未实现对象思想，应该就是全自动，返回一个结果封装好的对象。
2.对数据量的算法太少，没有大数据的支持，比如我这套中的源码，简单对数据量的多少自动实现了不同的敏感度（就是对3σ）的数字3进行放大或者缩小，
在目前来说，一组数据中，3<个是没有必要异常值查找的，3~8用1σ准则，8~11用2σ准则，>11用3σ准则。
3.代码上存在有逻辑不严谨的地方。
4.后面我会完善代码和编写文档，不会和错误的地方太多。
5.希望有大数据研究，和我一起来发展这个算法框架的欢迎一起开发vx 13195530002 ，许多不足的地方欢迎指正 584137831@qq.com   

# 在此谢谢大家~
