# eureka-service

##启动类添加注解
@EnableEurekaService

##在注册中心添加两个配置文件application-peer1.yml, application-peer2.yml，分别用于启动两个注册中心，内容如下
```yaml
  spring:
    application:
      name: eureka-server
  server:
    port: 8111
  eureka:
    instance:
      hostname: register1
    client:
      register-with-eureka: true
      serviceUrl.defaultZone: http://register2:8112/eureka/
```
```yaml
  spring:
    application:
      name: eureka-server
  server:
    port: 8112
  eureka:
    instance:
      hostname: register2
    client:
      register-with-eureka: true
      serviceUrl.defaultZone: http://register1:8111/eureka/
```
在/etc/hosts文件中添加peer1，peer2的ip转换
```text
  127.0.0.1 register1
  127.0.0.1 register2
```
