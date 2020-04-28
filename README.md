1.添加activiti的pom依赖
2.如果项目加入了mybatis 通用mapper，需要排除persistence-api
3.SpringBoot集成activiti默认会从classpath下的processes目录下读取流程定义文件，
所以需要在src/main/resources目录下添加processes目录，并在目录中创建流程文件
4.启动类，注意@SpringBootApplication注解需要设置exclude属性
5.spring:
    activiti:
      check-process-definitions: false #自动检查、部署流程定义文件
      database-schema-update: true #自动更新数据库结构
      #流程定义文件存放目录
      process-definition-location-prefix: classpath:/processes/ 
      #process-definition-location-suffixes: #流程文件格式
6.mysql版本需要在8以下,选择5的版本,防止找不到schema
7.HikariPool-1 - Shutdown initiated... 问题
    引入:spring-boot-starter-web即可