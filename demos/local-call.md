> ![warning](../sources/images/check.gif)本地调用，使用了Injvm协议，是一个伪协议，它不开启端口，不发起远程调用，只在JVM内直接关联，但执行Dubbo的Filter链。

定义 injvm 协议:

```xml
<dubbo:protocol name="injvm" />
```

设置默认协议:

```xml
<dubbo:provider protocol="injvm" />
```

设置服务协议:

```xml
<dubbo:service protocol="injvm" />
```

优先使用 injvm:

```xml
<dubbo:consumer injvm="true" .../>
<dubbo:provider injvm="true" .../>
```

或

```xml
<dubbo:reference injvm="true" .../>
<dubbo:service injvm="true" .../>
```

> ![warning](../sources/images/warning-3.gif)注意：服务暴露与服务引用都需要声明 `injvm="true"`

##### 自动暴露、引用本地服务

从 dubbo 2.2.0 开始，每个服务默认都会在本地暴露。在引用服务的时候，默认优先引用本地服务。如果希望引用远程服务可以使用一下配置强制引用远程服务。

```xml
<dubbo:reference ... scope="remote" />
```