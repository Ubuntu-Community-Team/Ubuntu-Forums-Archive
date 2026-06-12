---
title: "my system is confused as to which java i have installed"
date: 2008-03-03
forum: Installation &amp; Upgrades
---

### Post by 1oki on 2008-03-03
Ok, so i installed java6-jre, and plugins ...

java -version returned java6. 

when i go to run a java webapp (logmein) it says i need the JRE plugin... I tried all of them... GCJ plugin, Java6 (says it's already installed) Java5 (java -version returns nothing when this is installed), GCJ (icedtea or something like that) and the only one that works is the regular GCJ plugin, which is old i imagine because the java test site:[http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml) is saying:

Vendor: GNU Classpath
Version: 1.4.2 
OS: Linux
OS version: 2.66.22-14-generic.



ok, to sum it up...

I have java6 jre installed, but it wont register. When a java program tries to open in firefox i get prompted to install a plugin and the only one that works is the GCJ plugin even though I have java6 installed... 

please help... :(

---

### Post by earobinson on 2008-03-03
try: [http://wiki.earobinson.org/index.php5?title=FAQ#How_do_I_use_java_1.6_on_Ubuntu.3F](http://wiki.earobinson.org/index.php5?title=FAQ#How_do_I_use_java_1.6_on_Ubuntu.3F)

---

### Post by taurus on 2008-03-03
In the URL address field, type

```
about:plugins
```
and see if Sun java 1.6 is on the list.

---

### Post by 1oki on 2008-03-03
Thanks for the fast reply both of you.... 

about: plugins didn't show anything except for the GCJ plugin. I uninstalled that and tried it again... Just to make sure that Java6 is installed I did another java -version with return of this:

> java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Client VM (build 1.6.0_03-b05, mixed mode, sharing)


it's almost like java is installed but the plugin for firefox isnt. But the Sun-Java6-Plugin is installed... hmmmmmm

Im checking out that wiki link now.

---

### Post by taurus on 2008-03-03
Did you remember to restart firefox?

---

### Post by 1oki on 2008-03-03
yeah I tried the wiki page and that didnt help me any...



yes I did restart firefox and still nothing... lol I think this is just fascinating... Frustrating, but fascinating at the same time :)

---

### Post by 1oki on 2008-03-03
everywhere I look it says i have java6 installed... Console under system tools,  plugin control panel, Policy tools. 


could there be something in the plugin control panel that I am missing?

---

### Post by 1oki on 2008-03-04
bump...


anyone?

---

### Post by 1oki on 2008-03-04
Never mind... Stupid symlinks..

I had to create this symlink:
/usr/lib/jvm/java-6-sun-1.6.0.03/jre/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/firefox/plugins


now firefox recognizes the plugin! 

cheers all!

---

