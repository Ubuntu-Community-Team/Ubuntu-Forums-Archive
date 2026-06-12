---
title: "Can't get java installed"
date: 2016-06-25
forum: Installation &amp; Upgrades
---

### Post by rva1945 on 2016-06-25
Hi:

I followed the guidelines at 
[http://www.java.com/en/download/help/linux_x64_install.xml#install](http://www.java.com/en/download/help/linux_x64_install.xml#install)

but only managed to have the folder and its contents. No install, no setup t run with xdg-open INSTALL.

java -version still gives 1.6.0_036.

Help, thanks!

---

### Post by QIII on 2016-06-25
Hello!

The very easiest method for installing Oracle Java in Ubuntu can be found [here]("http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html").

Andrei has created a script that does the downloading, installing, EULA signing, etc, all without any effort on your part.  Best thing is that when Oracle updates Java, Andrei updates his PPA so you get updated.

---

### Post by rva1945 on 2016-06-25
Thanks, it worked like a charm!

---

