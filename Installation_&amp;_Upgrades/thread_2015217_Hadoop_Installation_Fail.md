---
title: "Hadoop Installation Fail"
date: 2012-07-02
forum: Installation &amp; Upgrades
---

### Post by huangyingw on 2012-07-02
Hi,
   I have downloaded hadoop_1.0.3-1_x86_64.deb from hadoop official website, and installed.
   After that, I use command ```
hadoop-setup-single-node.sh
```, to setup single node. And during all the process, use the default option.
   But failed with lots of "chown: invalid user: `mapred:hadoop'". Seems that, the hadoop user and group should be created during installation.
   So, there is some problem with installation?
   My Ubuntu version is 12.04 64 bit, java version as bellow:
```
root@ssd:/home/huangyingw# java -version
java version "1.6.0_24"
OpenJDK Runtime Environment (IcedTea6 1.11.1) (6b24-1.11.1-4ubuntu3)
OpenJDK 64-Bit Server VM (build 20.0-b12, mixed mode)
root@ssd:/home/huangyingw#
```.

---

