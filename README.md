# Maven学习笔记

-- 本地文件路径：/e/workspaces/atom/maven-useful
-- test

## 总结
 - 依赖管理，对 jar 包的统一管理（pom，dependency）
 - 项目构建，对项目信息，项目清理，编译，测试...功能实现（生命周期，插件）

## 环境搭建
 - MAVEN_HOME
 - Path(可以直接写绝对路径，有时候不能使用原因情况下)
 - MAVEN_OPTS(包括language，urf-8，512M等内容)

## 编写 $MAVEN_HOME/conf/setting.xml
 - 项目，本地仓库，中央仓库，私服nexus
 - xml 中配置，localRepository, mirror, server, property
 - 配置好的 xml 强烈建议保存下来，以免丢失又重新查找内容编写，前天重装系统就没有了

## 目录树
 - src
    - main
      - java
      - resources
      - webapp(javaweb项目的话有)
    - test
      - java
      - resources
 - pom.xml
 - target (后来项目编译之后自动产生)

## 命令
 - clean
 - complie
 - test
 - package
 - install
 - deploy
 - site
 - 对应三个生命周期（Clean, Default, Site LifyCycle）

## M2Eclipse
 - perferences 中 maven 修改 (installations和 user settings)
 - 注意可以 show view 然后 maven repository 中 local repository 右键创建索引，这样建立 dependency 时候就很快看到本地有哪些文件
 - maven project 普通 maven 工程和父工程
 - maven module 子工程
 - snapshot 快照   releases 正式发行版

## 依赖范围

 haha | 对于编译的 classpath 有效 | 对测试的 classpath 有效 | 对运行的 classpath 有效 | 例子
 :----:|:----:|:----:|:----:|:----:|
 compile | y | y | y | spring-core-4.3.9.jar
 test | n | y | n | junit
 provided | y | y | n | servlet-api-3.1.jar
 runtime | n | y | y | JDBC驱动
 system | y | y | n | 本仓库之外的类库

注意：run as maven build 来定义命令执行（如：tomcat:run 或者 deploy:e）

## pom.xml 中的信息
 - 项目信息内容展示
 - dependency
 - 构建 plug-in
 - maven 软件的目录树
    - bin
    - boot 类加载框架
    - conf xml 文件和 logging 文件夹
    - lib 很多 jar 包
    - licence，notice，readme.txt 对 maven 版本等信息文件
 - GBK 出错时，记得设置 utf-8

## maven 坐标

groupId（组织名）/artifactId（包名）/ version / artifactId-version.packaging

## 父工程中包含很多子模块，项目之间的继承

通过 module 来聚合，通过父子级的 pom.xml 来继承依赖管理

## nexus 私服，安装，配置，更新索引，并本地上传，下载 jar 包到 nexus
 - 通过命令行模式和 IDE 模式来熟练操作，理解 maven ，生成 jar 包，使用到另一个项目中
