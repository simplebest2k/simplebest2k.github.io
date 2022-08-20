---
title:  "리모트 파일 존재여부를 확인"
excerpt: "Java를 이용한 원격 파일 유무 확인"

categories:
  - Blog
  - Java
tags:
  - Java
  - Programming
classes: wide  
last_modified_at: 2021-07-28T16:30:00
toc: true
toc_label: "목차"
toc_icon: "bookmark"
author_profile: true
sidebar:
  nav: "main"
---
원격 파일의 존재여부만 간단하게 확인할 수 있는 방법으로 단순하게 사용되는 일반적인 방식이다.

> JDK : 11<br>
> 개발툴 : JetBrains IntelliJ Ultimate<br>
> Spring Boot : 2.5.2

```java
public class RemoteFileChecker {
    @Test
    void exists() throws IOException {
        String urlName = "http://localhost:8080/test/image.png";
        var connection = (HttpURLConnection)new URL(urlName).openConnection();
        connection.setRequestMethod("HEAD");

        var result = (connection.getResponseCode() == HttpURLConnection.HTTP_OK);
        System.out.println("check result => " + result);
    }
}
```

참고로, response code를 이용하면 다양한 형태로 리모트 리소스의 상태를 확인할 수 있다.