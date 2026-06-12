---
title: "My guess I have three JRE's installed, but I can't see the first I installed."
date: 2005-06-18
forum: Installation &amp; Upgrades
---

### Post by silent-red on 2005-06-18
First I was installing firefox java plugin which is Jre1.5_0_02 following the ubuntuguide (apt-get install), then I want to install the Java SDK so I search the web and found a nice tutorial on how to install j2sdk1.5 the latest version and update.

The tutorial can be found in here [http://www.codefez.com/Home/tabid/36/articleType/ArticleView/articleId/125/InstallingtheJava15JDKonLinspire.aspx;](http://www.codefez.com/Home/tabid/36/articleType/ArticleView/articleId/125/InstallingtheJava15JDKonLinspire.aspx;)

I was hoping when I  [test the runtime environment](http://java.com/en/download/help/testvm.xml)  that I have the latest 1.5.0_03 of jre but what I see is the previous jre1.5.0_02 or update 2. 

Using the command: >>>update-alternatives --config java
Heres what I see, at least there two RE```
There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/lib/j2re1.5-sun/bin/java
*+    2        /usr/lib/j2sdk1.5-sun/bin/java
``` 

From what I know there are two JRE's on J2SDK, one separate(at least on windows this is used in running applets) and one bundled with the SDK. 


Where could I find the first JRE I installed using apt-get?
 Are there previous reported problems that could occur with this setup? As of now, My machine is running smoothly.

---

