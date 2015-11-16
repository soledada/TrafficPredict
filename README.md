# TrafficPredict
Alibaba Tianchi bigdata competition of Intelligent traffic

this file just write in chinese

该目录主要模块和文件夹内容：
模块
1.fileReadyWork.py
原始文件预处理模块。
对原始数据进行处理，生成对每个小时统计的数据文件train_hour_stat文件夹和只对原始数据进行数字处理（未统计）的train_prosrc文件夹。
两个文件夹中都有allLine.txt，其中包括所有公交线路
train_hour_stat一行包含[次数，天数，周数，星期，小时，月，日]
train_prosrc一行包括[天数，周数，星期，小时，月，日，终端号，卡号]

2.buildTrainTestFile.py
切割处理好的数据文件成21份。
同时可以一键得到某一份数据

3.buildFeatureVec.py
生成特征向量，供预测

4.predictResult.py
预测算法，可以使用线性回归，泊松分布，RNN等

5.checkResult.py
准确率检测

6.Constant.py
常数模块，方便调参

7.main.py
主控制模块

目录：
1.src_data
原始文件

2.train_hour_stat
统计处理原始文件，包括allLine.txt所有线路文件。
每条线路都有一个txt文件，其中格式为：
[次数（count），天数（rday），周数（week），星期（day），小时（hour），月（month），日（date）]
如[100,0,0,4,12,8,1] 代表 第0天，第0周，周五，12点，8月1日，有100上车

3.train_prosrc
统计处理原始文件，包括allLine.txt所有线路文件。
每条线路都有一个txt文件，其中格式为：
[天数（rday），周数（week），星期（day），小时（hour），月（month），日（date），终端号（tid），卡号（cid）]
相当于对原始数据进行处理

4.train_test
对统计的数据进行处理，其中有n=21个文件夹，每个文件夹对应一份切割好的数据，格式同train_hour_stat。
对于每一份数据，天数（rday）是从切分开始日期算起的。
如第0份数据中，第0天为8月1日。（训练日期为8月1日~12月4日）
在第1份数据中，第0天为8月2日。（训练日期为8月2日~12月5日）
对每一份数据文件（对应每条公交线路）都有一份测试文件，如'test10.txt'，为训练文件后7天的真实数据
