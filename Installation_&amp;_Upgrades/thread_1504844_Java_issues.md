---
title: "Java issues"
date: 2010-06-08
forum: Installation &amp; Upgrades
---

### Post by Estrix on 2010-06-08
I've read through many of the Java issue posts here and am still stuck. Whenever I attempt to run a web page that requires java, firefox crashes. I've just downloaded the sun java 6.0 plugin, and I'm running firefox version 3.6.3. The opperating system is Ubuntu 10.04.

typing about:plugins into firefox shows that java is there. Running as root, java -version displays
java version "1.6.0_20"
Java(TM) SE Runtime Environment (build 1.6.0_20-b02)
Java HotSpot(TM) Client VM (build 16.3-b01, mixed mode, sharing)

So as far as I can tell it should be working. Any help would be greatly appreciated.

---

### Post by Backharlow on 2010-06-08
In Firefox, go Addons > Plugins
is there something there for java?
I have icedtea listed there.
You might try
apt-get install icedtea6-plugin
restart firefox
go to [http://www.javatester.org/version.html](http://www.javatester.org/version.html)
and see if the web applet there pops up.

---

### Post by Estrix on 2010-06-08
Under Add-Ons I've got Java Console 6.0.20. Does Icedtea support the latest java?

Tried IcedTea plugin and then went to the test pages as suggested, the web applet stays blank. I tried it on other applets with the same effect (nothing lol)

---

### Post by ell02 on 2010-06-08
Applets are funny,this allways fixes me up for pogo.

[https://sites.google.com/site/easylinuxtipsproject/java](https://sites.google.com/site/easylinuxtipsproject/java)

Looks hard but it's not.

---

