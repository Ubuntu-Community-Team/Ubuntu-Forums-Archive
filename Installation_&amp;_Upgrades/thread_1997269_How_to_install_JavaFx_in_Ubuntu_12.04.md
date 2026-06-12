---
title: "How to install JavaFx in Ubuntu 12.04?"
date: 2012-06-04
forum: Installation &amp; Upgrades
---

### Post by antoaravinth on 2012-06-04
I download JavaFx from [here]("http://www.oracle.com/technetwork/java/javafx/downloads/devpreview-1429449.html"). I placed it in my home directory(anto) under the name javafx. Then I did something like this :

vi ~/.bashrc

and added the following lines:

javaFx_home=/anto/javafx/rt/lib/jfxrt.jar
export PATH=$PATH:$javaFx_home

But after providing the classpath, I tried running :

groovy MyProgram
(which depends on the JavaFx classpath).

But that throws me an error, stating that JavaFx can't be found. Where I went wrong?

---

### Post by virpara on 2012-06-08
Give output of ```
ls /anto/javafx/
```

---

### Post by antoaravinth on 2012-06-12
I get output like this : 

> bin             docs  README.html  THIRDPARTYLICENSEREADME.txt
COPYRIGHT.html  lib   rt           tools

---

