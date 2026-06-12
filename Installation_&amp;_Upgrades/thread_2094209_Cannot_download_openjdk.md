---
title: "Cannot download openjdk"
date: 2012-12-13
forum: Installation &amp; Upgrades
---

### Post by shahalpk on 2012-12-13
while i try to install openjdk via

```
sudo apt-get install openjdk-7-jdk
```

It start downloading ,bt will not go beyond 10% for the following file
[http://mirrors.kernel.org/ubuntu/pool/universe/o/openjdk-7/openjdk-7-jre-headless_7u9-2.3.3-0ubuntu1~11.10.1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/universe/o/openjdk-7/openjdk-7-jre-headless_7u9-2.3.3-0ubuntu1~11.10.1_i386.deb)

same is the case for several files.
my system is behind a proxy and everything else works fine.

why does this happen?

Same happens if i try to download it via firefox/chrome/wget/curl for the above file. is something wrong with the mirrors? should i change some settings?

---

### Post by dino99 on 2012-12-13
[http://packages.ubuntu.com/en/quantal/i386/openjdk-6-jre-headless/download](http://packages.ubuntu.com/en/quantal/i386/openjdk-6-jre-headless/download)

maybe your used mirror is borked/down/else

---

