# -
道路交通智能监控系统
《道路交通智能监控系统》用户手册
一、系统环境配置 训练平台：南京工业大学高性能服务中心 GPU：Tesla V100 32GB， 测试平台：Nvidia GeForce GTX 3090 本系统是基于 Ubuntu18.04 系统下配置，采用 paddlepaddle-gpu2.3.1+cud atoolkit11.2+cuDNN 8.1.1+opencv4.4.0.46 二、下载安装及调试 paddle
二、下载安装及调试 paddle 1）安装 paddle 按照服务器的显卡型号，在百度飞浆官网就可找到对应的 paddle 框架的 gpu 以及 cuda 版本号 比如：显卡型号为 Nvidia GeForce GTX 3090，找到官网对应的 paddle 版 本号，其下载指令为![image](https://user-images.githubusercontent.com/104422714/187149618-c9cb24aa-7fb0-466e-bab1-1a36bb1f5abe.png)
2）调试安装 验证是否安装成功：使用 python3 进入 python 解释器， 输入 import paddle.fluid 再输入 paddle.fluid.install_check.run_check()。 如果出现 Your Paddle Fluid is installed successfully!，说明已成功 安装。3）修改配置文件 GPU=1 #如果使用 GPU 设置为 1 CPU 设置为 0 CUDNN=1 #如果使用 CUDNN 设置为 1，否则为 0 OPENCV=0 #如果调用摄像头，还需要设置 OPENCV 为 1，否则为 0 OPENMP=0 #如果使用 OPENMP 设置为 1，否则为 0 DEBUG=0 #如果使用 DEBUG 设置为 1，否则为 0
三、交通状况检测1.基于 Paddle 的 YOLOv5 算法检测视频监控画面中的车辆与行人； 2.基于 Paddle 的 DeepSort 算法对检测到的车辆进行跟踪并生成运动轨迹； 3.根据车辆检测与跟踪的结果 ，结合传统计算机视觉方法，实现了车流量 统计、多种交通违章行为(占用应急车道、违法越线变道、行人闯入)的实时自动 检测、撞车事故、道路拥堵检测
运行 track.py 文件，实现了车流量统计、多种交通违章行为(闯红灯、违法 变道、卡车违法占道行驶、行人闯入)的实时自动检测、道路拥堵检测。通过人 机界面将识别结果实时反馈给工作人员，实现道路交通的智慧化和可控化
