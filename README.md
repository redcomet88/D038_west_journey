# D038 vue+django西游记问答知识图谱可视化系统

> 完整项目收费，可联系QQ: 81040295 微信: mmdsj186011 注明从github来的，谢谢！
也可以关注我的B站： 麦麦大数据 https://space.bilibili.com/1583208775
> 

up主B站：  **麦麦大数据**
关注B站，有好处！

编号:  D038
## 视频
[视频链接]()
## 1 系统简介
本系统是一个基于Vue和Django构建的"西游记智能问答知识图谱可视化系统"，旨在为用户提供一个结合知识可视化与智能问答的学习平台。其核心功能包括：数据文件管理、知识图谱构建与可视化、智能问答以及用户管理模块。系统通过数据文件管理模块获取西游记相关信息，构建知识图谱以展示人物关系、事件序列等信息，并通过可视化界面让用户直观理解。同时，系统提供智能问答功能，支持用户就西游记内容提出问题并获取智能回答。用户管理模块则包含登录、注册和个人设置功能，确保用户能够安全访问系统并个性化定制使用体验。## 2 功能设计
该系统采用B/S架构模式，分为前端和后端两个部分。前端使用Vue.js框架构建，结合Vuex进行状态管理，Vue Router实现路由导航，ECharts用于数据可视化。后端采用Django框架构建RESTful API，处理业务逻辑，并与MySQL数据库和Neo4j图数据库进行交互。MySQL数据库主要用于存储结构化的用户信息和人物数据，Neo4j则用于存储人物之间的关系和图谱结构。系统还引入了爬虫模块，用于抓取相关数据，并通过蒸汽姿态API获取人物立绘。整个系统强调用户体验，通过统一的API接口和模块化设计，确保系统的可扩展性和维护性。
### 2.1系统架构图
该系统采用典型的B/S（浏览器/服务器）架构模式，前端通过Vue.js生态系统构建，包括Vue Router（用于路由导航）、Vuex（用于状态管理）和Echarts（用于数据可视化），为用户提供交互式、直观的界面体验。后端基于Django框架开发，利用Django REST framework构建API接口，负责业务逻辑处理和数据交互。系统搭配MySQL数据库进行数据存储，使用Django ORM进行数据持久化操作。知识图谱的构建和智能问答功能则依赖于数据处理模块，该模块通过解析数据文件中的西游记相关信息，构建实体关系模型，并结合自然语言处理技术（如NLTK、spaCy等）实现智能问答功能。用户管理模块则提供安全的登录注册功能，并支持个人信息和头像的管理，确保用户体验的个性化和安全性。
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/943c1edaa3094dd9929cdf61193202c0.png)
### 2.2 功能模块图
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/13cf13612fdf4676886de6f51c73b797.png)
## 3 功能展示
### 3.1 登录 & 注册
登录界面背景是一个视频，展示和本文系统主题相匹配的内容，登录和注册界面在一个界面下，通过按钮来切换，注册界面输入用户名和密码，会检查这个用户是否存在，登录界面则要检查用户名是否存在以及用户名密码是否正确：  
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/00263f84a3cf482ebc50ac1ffbbc51ae.png)
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/873bf411819747ffa76d3f1d6ff5c025.png)
### 3.2 知识图谱构造
如果通过校验，则可以进入主页，在主页是一个左侧菜单，右侧操作面板的布局，右上角是登录用户的头像和退出按钮：
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/d971217028c049f4936cc20383ce20cc.png)
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/3e07da11a65c4b86b47ee49129566e85.png)

### 3.3 知识图谱可视化
知识图谱可视化支持搜索：
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/4d02f6a3cbc84927b028c8dba4eabf85.png)
### 3.4 智能问答
基于LTP模型的问答系统实现，可以根据知识图谱，咨询人物和人物关系具体在后面有代码介绍：
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/8e7c2791b4cb4b148f2fd4e91b9f6ecd.png)
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/c348956dc3f44b62adb2cc0d955cea67.png)
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/0f1440b3dd2043ebb640c5d9cda2f09f.png)
### 3.5 个人设置
个人设置方面包含了**用户信息修改**、**密码修改**功能。
用户信息修改中可以上传头像，完成用户的头像个性化设置，也可以修改用户其他信息。
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/63090eba53fa4c54ba5873dcf9997624.png)
修改密码需要输入用户旧密码和新密码，验证旧密码成功后，就可以完成密码修改。
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/c1ab553499ff4b029e5a2f976fcaa3a7.png)
## 4程序代码
### 4.1 代码说明
代码介绍：基于LTP的西游记人物问答小应用的实现。该应用可以回答关于西游记人物的基本信息，如角色、别名、性格特点等问题
### 4.2 流程图
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/8c194ead6ba84c719e340e094848371f.png)
### 4.3 代码实例
```python
import ltp
import numpy as np

# 加载LTP模型
LTP_MODEL_PATH = "model"
segmentor = ltp.Segmentor()
segmentor.load_with_lexicon(LTP_MODEL_PATH + "/cws.model", LTP_MODEL_PATH + "/lexicon.txt")

# 西游记人物知识库
characters = {
    "孙悟空": {"role": "主角", "alias": "齐天大圣", "personality": "勇敢、机智"},
    "猪八戒": {"role": "二当家", "alias": "天蓬元帅", "personality": "好吃懒做"},
    # ...更多角色
}

def get_character_info(question):
    # 分词
    words = segmentor.segment(question)
    # 提取人物实体
    for word in words:
        if word in characters:
            return characters[word]
    return None

# 示例使用
question = "孙悟空的别名是什么？"
info = get_character_info(question)
if info:
    print(f"{question} 的回答是：{info['alias']}")
else:
    print("没有找到相关信息。")

```
