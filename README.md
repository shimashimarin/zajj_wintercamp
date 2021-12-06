# 重复 VBS ZGamma 分析
基于 CMS Full RunII VBS ZGamma 分析：[arxiv:2106.11082](https://arxiv.org/abs/2106.11082)

## 环境设置

### 使用 `JupyterHub`  （推荐）

北大服务器团队已经搭建了好了 `JupyterHub` 服务，可以通过访问 https://hepfarm02.phy.pku.edu.cn:5201/ ，使用服务器临时账号和密码登录。如遇证书问题，不能打开页面，建议切换其他浏览器，如 [firefox](http://www.firefox.com.cn/)。

### 本地安装环境

如上述方法使用存在问题，可以登录服务器账号，自己设置环境。方法如下 （参考 [install miniconda](https://conda.io/projects/conda/en/latest/user-guide/install/index.html)），

1. 登录临时服务器账号，运行命令

```bash
wget https://repo.anaconda.com/miniconda/Miniconda3-py39_4.10.3-Linux-x86_64.sh
bash Miniconda3-py39_4.10.3-Linux-x86_64.sh
conda create --name myenv python=3.9.4
conda activate myenv

pip install awkward coffea numpy numba uproot matplotlib \
boost_histogram mplhep pyhf jupyter ipywidgets jupyterlab cabinetry[contrib]

# 打开jupyter notebook，注意：--port 后面的参数，大家任取2位～4位数字，大家同时用一个端口，会引起冲突

jupyter notebook --no-browser --port 7777 

# 在输出信息中，找到URLs

```

2. 重新在本地打开一个终端，运行命令

```
ssh -L 7777:localhost:7777 atlas
```
3. 将URLs复制粘贴至浏览器打开。

## 课程内容

本课程主要由3个notebook文件组成，分别包含，对预处理样本做事例筛选(`select_events.ipynb`)，画图 (`plotting.ipynb`)，和统计分析(`statistics.ipynb`)。

### 获取课程材料
登录 `JupyterHub` 或者自己建立jupyter notebook，在右侧 `new` 下拉菜单栏，选取`Terminal`，进入终端。

```bash
git clone https://github.com/shimashimarin/zajj_wintercamp.git
cd zajj_wintercamp
```

如不能下载，可以直接从已有目录中拷贝：

```bash
mkdir zajj_wintercamp
cd zajj_wintercamp
cp /home/pku/songyx/jiexiao/wincamp/*ipynb .
cp /home/pku/songyx/jiexiao/wincamp/config_histograms.yml .
```

点击左上角 `JupyterHub` 图标，回到查看目录页面。

### 测试课程材料
依次打开并运行`notebook`文件，`test_env.ipynb`，`select_events.ipynb`，`plotting.ipynb`，和 `statistics.ipynb`。

> 打开 notebook 文件后，需要先在左侧顶栏，在 `Kernel` 复选框中，选择 `Python [conda env:wintercamp]`，其他选项环境设置不同，会导致运行失败。
>

