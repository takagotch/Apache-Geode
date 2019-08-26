### apache-geode
---
https://github.com/apache/geode

https://geode.apache.org/

```java
import java.util.Map;
import
import

public class HelloWorld {
  public static void main(String[] args) throws Exception {
    ClientCache cache = new ClientCacheFactory()
      .addPoolLocator("localhost", 103334)
      .create();
    Region<String, String> region = cache
      .<String, String>createClientRegionFactory(ClientRegionShortcut.CaCHING_PROXY)
      .create("hello");
      
    region.put("1", "Hello");
    region.put("2", "World");
    
    for (Map.Entry<String, String> entry : region.entrySet()) {
      System.out.format("key = %s, value = %s\n", entry.getKey(), entry.getValue());
    }
    cache.close();
  }
}
```

```build.gradle
apply plugin: 'java'
apply plugin: 'application'

mainClassName = 'HelloWorld'

repositories { mavenCentral() }
dependencies {
 compile 'org.apache.geocode:geode-core:1.4.0'
 runtime 'org.slf4j:slf4j-log4j12:1.7.24'
}
```

```sh
gradle run
```


