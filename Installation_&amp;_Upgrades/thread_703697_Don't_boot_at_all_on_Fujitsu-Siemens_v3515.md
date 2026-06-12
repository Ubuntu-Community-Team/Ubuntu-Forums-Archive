---
title: "Don't boot at all on Fujitsu-Siemens v3515"
date: 2008-02-21
forum: Installation &amp; Upgrades
---

### Post by devel on 2008-02-21
Hello, 

I have Fujitsu-Siemens Amilo Pro v3515. 

I would like to install Ubuntu 7.10 on it. 

I put a CD, it boots, but when it is going to load graphic (desktop) it just shows black screen and one a minute the mouse pointer appears for few seconds... 

The situation is similar on other distribiutions, such as Fedora or Mint. 

I think that it would be usefull to execute "dpkg-configure xserver -xorg", but I can't either access to text mode by pressing Ctrl+F1 - nothing happens. 

Please help me, I lost more than 10 hours on it...

---

### Post by dstew on 2008-02-21
The key combination is ctrl-alt-F1. However, if you are having trouble getting the Live CD to boot, try the Alternate Install CD. It installs the same Ubuntu system, but uses a text-based installer that works more reliably. Get if from the [Ubuntu Downloads page]("http://www.ubuntu.com/getubuntu/download"), just click the box below the Start Download button.

---

### Post by devel on 2008-02-22
Is there other possibility to install ubuntu not using alternate version? In fact I would like to install Linux Mint, which doesn't have alternate version...

---

### Post by dstew on 2008-02-22
There are basically three ways to install Ubuntu: The Live CD, the Alternate Install CD, and over the internet. To install over the internet you use the [unetbootin utility]("http://lubi.sourceforge.net/unetbootin.html"). If you want to try the internet installation, I recommend installing the base (server) edition first, with the generic kernel, and after that is installed, you can install the Ubuntu Desktop from a command line using apt-get.

---

