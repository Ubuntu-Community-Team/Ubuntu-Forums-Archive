---
title: "A few ubuntu-newbie questions"
date: 2005-05-11
forum: Installation &amp; Upgrades
---

### Post by patrik1982 on 2005-05-11
I've been using Gentoo for a while, but I felt I wanted to try ubuntu.

I have a few questions. Most of them are probably very simple to answer, but I can't find explicit answers anywere:

1) How do I configure my internet connection? I can set up my IP/gateway address, but I don't know where to enter the DNS info. I tried editing /etc/resolv.conf, but the next time i booted my changes were undone.

2) How do I get apt-get to work? (never used debian-based distro before) If I understand it correctly, it automatically downloads and install the requested software (much like emerge in Gentoo)

3) How do I install the kernel sources? As I'm using a clean Hoary-install, I'm using the 2.6.10-5 kernel. I want to be able to configure it the way I'm used to (by typing "make menuconfig").

Please, help me answer these questions.

---

### Post by Gags666 on 2005-05-11
Hi follower,

I came from Gentoo, too. :) With 1) I can't help you because my network was alright from the beginning and with 3) I also can't help because I didn't try this yet with Ubuntu. :)

[quote="patrik1982"]2) How do I get apt-get to work? (never used debian-based distro before) If I understand it correctly, it automatically downloads and install the requested software (much like emerge in Gentoo)[/quote]
apt-get manages your packages like emerge. ```
apt-get update
``` can be compared with ```
emerge sync
``` It updates the repositories. With ```
apt-get upgrade
``` all the installed packages will be updated if necessary. If you want to install a new package you can search the repository with ```
apt-**cache** search searchstring
``` and when found the right one install it with ```
apt-get install packagename
``` But you can also use a GUI for apt-get called Synaptec and the Update-Manager. They're already included in Ubuntu and should be self-explanatory in their use.

In /etc/apt/sources.list you can find the repositories for apt-get. I added the ones from the [Ubuntu Backports Project](http://backports.ubuntuforums.org/) and removed the "#" from the already included ones. Works fine for me.

Hope I could help. :)

---

### Post by tonym on 2005-05-11
[QUOTE=patrik1982]3) How do I install the kernel sources? As I'm using a clean Hoary-install, I'm using the 2.6.10-5 kernel. I want to be able to configure it the way I'm used to (by typing "make menuconfig").[/QUOTE]

See [http://www.ubuntulinux.org/wiki/KernelHowto](http://www.ubuntulinux.org/wiki/KernelHowto)

---

### Post by patrik1982 on 2005-05-11
[QUOTE=tonym]See [http://www.ubuntulinux.org/wiki/KernelHowto](http://www.ubuntulinux.org/wiki/KernelHowto)[/QUOTE]
Thank you

---

### Post by az on 2005-05-11
That howto is for Warty.  In hoary, use the linux-tree package....

---

