#一些汉语言处理的东西

## segment 汉语言分词
- 原理：HHM
- 依赖：numpy scipy hhmlearn 
- 参考：
http://www.52nlp.cn/itenyh%E7%89%88-%E7%94%A8hmm%E5%81%9A%E4%B8%AD%E6%96%87%E5%88%86%E8%AF%8D%E5%9B%9B%EF%BC%9Aa-pure-hmm-%E5%88%86%E8%AF%8D%E5%99%A8
http://sbp810050504.blog.51cto.com/2799422/1251640
- TODO：
    没有针对英文单词、标点等处理，也没有窗口化操作

	
## 主题分类
- 原理：LDA & Labled LDA
- 依赖：gensim
- 参考:
http://blog.itpub.net/16582684/viewspace-1253901/
https://radimrehurek.com/gensim/models/ldamodel.html
https://shuyo.wordpress.com/
- TODO:
	感觉效果不是很好啊

## 情感分析
- 原理: 基于统计的方式
- 依赖：ntlk sklearn
- 语料：某东的商品评论，好评-差评
- 参考：
http://rzcoding.blog.163.com/

## 贝叶斯分类
- 用C/C++重新实现后，发现内存占用率和运算速度比Python要块很多。
- 通过Sogou的训练语料发现，10个分类下，10000特征词的分类准确率在75%左右，而在京东抓取的好评/差评语料训练后，测试分类精度达到91%左右。

## 最大熵分类器
- 原理：自行Google
- 参考：
http://www.fuqingchuan.com/2015/03/776.html
http://www.nltk.org/_modules/nltk/classify/maxent.html
http://www.umiacs.umd.edu/~hal/megam/index.html
- NOTE：
基本是按照nltk的GIS算法翻译过来的，没有实现IIS，所以训练的速度非常的慢。
- MEGAM
添加了MEGAM部分，底层调用的megam是基于L-BFGS实现的，所以速度还是挺快的，有实用价值了。另外底层调用的megam是
二进制程序（32位）的，所以你的系统要支持32位的运行库（dnf install glibc.i686）

# 深度学习部分
## 依赖和使用的深度学习库
theano (CUDA optional)
keras
genism

## 深度学习分词
- 参考：
http://xccds1977.blogspot.com/2015/11/blog-post_25.html
- 语料库
http://www.sighan.org/bakeoff2005/ [北大和微软研究院的分词语料]
- TODO:
对于英文单词和数字的处理
加大神经网络的神经节点数目
- 分词效果(LSTM 100-100 4类标注 15次迭代):
``` 中东 和平 的 建设者 、 中东 发展 的 推动 者 、 中东 工业化 的 助 推 者 、 中东 稳定 的 支持者 、 中东 民心 交融 的 合作 伙伴 —— 习近 平 主席 在 演讲 中 为 中国-中东关系 发展 指明 的 方向 ， 切合 地区 实际 情况 ， 照顾 地区 国家 关切 ， 为 摆 在 国际 社会 面前 的 “ 中东 之 问 ” 给 出 了 中国 的 答案 。 
2014年6 月 ， 习近 平在 中 阿 合作 论坛 北京 部长 级 会议 上 提出 ， 中 阿 共建 “ 一带 一路 ” ， 构建 以 能源 合作 为 主轴 ， 以 基础 设施 建设 、 贸易 和 投资 便利 化 为 两翼 ， 以 核能 、 航天 卫星 、 新 能源 三 大 高 新 领域 为 新 的 突破口 的 “ 1 + 2 + 3 ” 合作 格局 。 
在 此次 落马 的 16 人 里面 ， 级别 最高 的 是 连 城县委 原 书记 江国河 。 履历 显示 ， 江 国河 196 3年 出生 ， 龙岩市 永定县 高头乡 人 。 被 调查 时 ， 他 已 在 福建省 能源集团有限责任 公司 董事 、 纪委 书记 的 位子 上 干 了 两年 。 
机智堂 是 新 浪 手机 推出 的 新 栏目 ， 风趣 幽默 是 我们 的 基调 ， 直白 简单 地 普及 手机 技术 知识 是 我们 的 目的 。 我们 谈 手机 ， 也 谈 手 机 圈 的 有 趣事 ， 每月 定期 更新 ， 搞 机 爱好者 们 千万 不 能 错过 。 
```

## RNN-LSTM自动文本生成
- 参考：
https://github.com/ebenolson/pydata2015/blob/master/4%20-%20Recurrent%20Networks/RNN%20Character%20Model%20-%202%20Layer.ipynb
https://github.com/karpathy/char-rnn
https://github.com/fchollet/keras/blob/master/examples/lstm_text_generation.py
