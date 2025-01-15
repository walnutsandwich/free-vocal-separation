# free-vocal-separation
免费在线使用人声伴奏分离工具 MSST-WebUI 的方法

如果在翻唱的时候，找不到合适的伴奏，不妨试试这款目前最新的声源分离工具。MSST-WebUI 是2024年最新的音乐源分离工具的界面版，操作简单，支持众多声源分离模型，您可以使用此Web界面推断MSST模型和VR模型来将 wav/mp3/flac等音频文件分离为人声和其他伴奏声音，还可以用于音频去噪、去混响、去和声，非常适用于音频制作领域。没有GPU电脑配置不高的小伙伴，如果想用该工具，推荐在【趋动云】平台上运行，下面注册启动项目即送算力点，做活动也可以获得算力点，可以免费使用数十小时。

注册链接：https://growthdata.virtaicloud.com/t/xK

右上角运行一下，确定克隆项目到自己空间，点击立即运行，服务器开启后点右上角进入开发环境。

![1](https://github.com/walnutsandwich/free-vocal-separation/blob/main/pics/%257B540F530C-A7B6-4304-836A-AF1555C50FD2%257D.png)

![1](https://github.com/walnutsandwich/free-vocal-separation/blob/main/pics/%7BE6FDD176-5B3B-4a63-8091-1A19924463DE%7D.png)

然后点击这里的Terminal 进入服务器命令界面：
![2](https://github.com/walnutsandwich/free-vocal-separation/blob/main/pics/%7B31131E30-C1E1-4693-A1C4-4AA29860DFBE%7D.png)

在 /gemini/code/ 目录下输入下面命令，确认执行即可启动。

bash start_msst.sh

等待一二分钟左右，可以看到命令行出现 Running on local URL:http://0.0.0.0:7860 表示webUI界面启动成功 
![2](https://github.com/walnutsandwich/free-vocal-separation/blob/main/pics/0.png)

此时可以在右侧新添加一个端口 7860 ，打开得到的外部访问连接，即可打开 MSST 的webUI 工作界面：

![2](https://github.com/walnutsandwich/free-vocal-separation/blob/main/pics/1.png)
![2](https://github.com/walnutsandwich/free-vocal-separation/blob/main/pics/2.png)

确定添加端口后，点击外部访问链接，即可进入在线的 MSST-WebUI 

![2](https://github.com/walnutsandwich/free-vocal-separation/blob/main/pics/3.png)


使用示例

在左侧的 Select model category 中选择 vocals_models, 右边 Select model 选择 model_bs_roformer_ep_368_sdr_12.9628.ckpt , 这是最推荐的人声伴奏分离模型。

下面一行选择默认的GPU，和输出音频格式，可以是 wav/mp3/flac 输出音频格式下面要选择要输出的分离结果，人声还是伴奏，或者两个都输出。
![3](https://github.com/walnutsandwich/free-vocal-separation/blob/main/pics/4.png)

再下方的 Use CPU 和 Using TTA 可以不勾选，然后在 Input audio 界面中上传音频文件（如果没有合适的可以先下载左边 /gemini/code/test.wav 上传做测试），音频可以是 wav/mp3/flac 格式，其他高级设置保持默认即可，如果要调batch大小（参考 12G 显存设置建议不超过 10），然后点击 最下方的 Input audio separation 按钮启动分离。
![3](https://github.com/walnutsandwich/free-vocal-separation/blob/main/pics/5.png)

分离过程中显存占用情况如下，大约等待跟该音频时长一样的时间后，该音频即可分离完成，请在左侧代码文件目录 /gemini/code/MSST-WebUI/results 文件夹下下载输出结果听听效果。

![3](https://github.com/walnutsandwich/free-vocal-separation/blob/main/pics/6.png)
![3](https://github.com/walnutsandwich/free-vocal-separation/blob/main/pics/7.png)

分离后的效果可以参考项目地址下方介绍中的音频试听：
![3](https://github.com/walnutsandwich/free-vocal-separation/blob/main/pics/QQ%E6%88%AA%E5%9B%BE20241203131227.png)

模型说明

常用的一些模型如下：

single_stem_models 中的 deverb_bs_roformer_8_256dim_8depth.ckpt去混响首选！也能去除部分和声！

single_stem_models 中的 denoise_mel_band_roformer_aufr33_sdr_27.9959.ckpth.ckpt是最新的降噪模型，推荐！

vocal_models 中的 model_bs_roformer_ep_368_sdr_12.9628.ckpt 分离人声伴奏推荐使用！

vocal_models 中的 model_mel_band_roformer_karaoke_aufr33_viperx_sdr_10.1956.ckpt 分离和声推荐使用！

multi_stem_models 中的 HTDemucs4_6stems.th 提取多轨可以使用，可以拆分出 drums,bass,other,vocals,quitar,piano 六种声音



个人推荐是大部分的歌曲，用 model_bs_roformer_ep_368_sdr_12.9628.ckpt 分离人声伴奏后，对人声再进行一次 deverb_bs_roformer_8_256dim_8depth.ckpt 去混响足够了。



更多模型和详细介绍，可以参考文档： https://r1kc63iz15l.feishu.cn/wiki/Dy0bwG4XIizBgJkePDucILaMnlf
