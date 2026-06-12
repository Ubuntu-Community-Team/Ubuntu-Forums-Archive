---
title: "installing java"
date: 2005-10-29
forum: Installation &amp; Upgrades
---

### Post by kc8pdr on 2005-10-29
How do I install java

---

### Post by stuporglue on 2005-10-29
Are you running on a Mac, or 64 bit machine? If not, it's pretty easy. 

1) Do you already have the universe repositories enabled? 

2) Will Java 1.4.2 do? Java 1.5 is newer, but Java 1.4.2 is easier to install.

If you said yes to both, just run

$ sudo apt-get install j2re1.4 

It'll install Blackdown Java 1.4.2 and mostly set it up. Once that's done, go to the Firefox plugin directory 

$ cd /usr/lib/mozilla-firefox/plugins

and make a link to the Java plugin. 

$ sudo ln -s /usr/lib/j2se/1.4/jre/plugin/i386/mozilla/libjavaplugin_oji.so .

Hope that helps!

---

### Post by kc8pdr on 2005-10-29
What is universe repositories enabled ?

---

