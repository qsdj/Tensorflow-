线性、逻辑回归。input_fn()建立简单两个特征列数据，用特证列API建立特征列。特征列传入LinearClassifier建立逻辑回归分类器，fit()、evaluate()函数，get_variable_names()得到所有模型变量名称。可以使用自定义优化函数，tf.train.FtrlOptimizer()，可以任意改动传到LinearClassifier。

随机森林。包含多个决策树分类器及回归算法。处理不平衡分类资料集，极大平衡误差。Kaggle数据科学竞赛，延伸版XGBoost。

TensorForestEstimator，tensor_forest.ForestHParams设置随机森林参数，多少棵树、节点数目上限、特征类别数目。

传进TensorForestEstimator初始化随机森林Estimator。数据特征列、类别列转换成float32格式，保证TensorForestExtimator训练更快拟合。Scikit-learn风格fit()方法。

随机森林容易过拟合，常用防止过拟合方法是损失减少的速度变慢或完全停止减少，提前停止模型训练。Monitor模块。random_forest模块自带LossMonitor。设定每隔100步Monitor检查损失减少速度，连续100次迭代损失没有减少，Monitor停止整个模型训练。

K均值聚类。多维空间每个点划分到K个聚类，每个点属于离它最近均值对应聚类。NumPy制造适合做聚类数据。make_random_centers函数随机生成num_dims个维度数据集聚类num_centers个中心点。make_random_points函数根据生成聚类中心点随便生成num_points个点。生成10000个点，6个随机聚类中心点。factorization模块KMeans初始化聚类方法，随机初始化RANDOM_INIT，传入RunConfig和、聚类中心数初始化KMeans Estimator对象，Scikit-learn风格fit()、predict()。KMeans clusters()函数看训练数据集每个点聚类分布。KMeans Estimator，predict()预测新数据点聚类，score()预测每个点和最近聚类距离总和，transform()计算每个点和模型判断聚类中心距离。

支持向量机。各种不同kernel或不同距离方程，针对不同特征数据建立不同线性及非线性模型。同时最小化经验误差与最大化几何边缘区，最大边缘区分类器。文本、图像分类。TF.Learn SVM Extimator API建立支持向量机模型。定义input_fn()建立有两个数据特征列、一个ID列、一个标识列模拟数据。contrib.layers FeatureColumn API 将feature1､feature2转换方便Estimator的FeatureColumn。特征列、ID列传入SVM初始化支持向量机，参数调节。l1_regularization、l2_regularization加正规化防止过度拟合问题(特征过多、例子不多，容易发生)。fit()、predict()。

DataFrame。TF.Learn包括独立DataFrame模块。类似Pandas、Spark、R编程语言DataFrame。提供TF.Learn读入数据迭代，读入各种数据类型(pandas.DataFrame、tensorflow.Example、NumPy)，FeedingQueueRunner数据分批读入，存在Queue，方便Estimator模型训练。NumPy eye()建简单对角矩阵，TensorFlowDataFrame.from_numpy()把NumPy矩阵转为TensorFlow DataFrame。可以像Pandas读入各种文件类型。

用TensorFlowDataFrame读入文件或数据类型后，run()制造数据批量(batch)生成器，Python yield生成generator，生成器维持数据列名和数据字典mapping。调节number_batches选择生成batch数量，选择性用自己的graph、session，数据batch存到session coordinator。batch()重新改变batch大小。数据洗一遍打乱顺序。split()，DataFrame分多个。select_rows()选择具体行数据。

监督器Monitors。TF.Learn自带Monitor，各种logging及监督控制训练过程。5个等级log，严重性最小到最大排列，DEBUG、INFO、WARN、ERROR、FATAL。选择只打印设置等级或更严重的log。TensorFlow默认log等级 WARN。模型训练log，设INFO。CaptureVariable 指定变量值存储到Collection。PrintTensor打印Tensor值。SummarySaver存储Summary协议缓冲(Protocol Buffer)。ValidationMonitor训练打印多个评估Metrics，监督模型训练，提前停止训练防止模型过度拟合。

TF.Learn自带learn.datasets.base.load_csv()读入CSV数据文件。定义评估模型metrics字典，contrib.metrics模块streaming_accuracy、streaming_precision、streaming_recall评估模型准确度、精确度、召回率。validation_metrics建立validation_monitor，提供评估数据及目标。提供every_n_steps指示每50步实行ValidationMonitor。validation_metrics传入metrics。early_stopping_netric提前停止监测metric。early_stopping_metric_minimize=True表明最小化前提供early_stopping_metric。early_stopping_rounds表明超过200步训练损失不减少，ValidationMonitor停止Estimator训练。

建立深度神经网络分类器DNNClassifier，三层神经网络，每层10､15、10个隐藏单元。分类器fit()指定监督器validation_monitor，指定多个监督器实现不同功能监督，validation_monitor，debug_monitor,print_monitor。

evaluate()、predict()，新数据评估模型准确度。

TF.Learn生成log及checkpoint文件可以直接读入TensorBoard可视化。

参考资料：
《TensorFlow实战》


