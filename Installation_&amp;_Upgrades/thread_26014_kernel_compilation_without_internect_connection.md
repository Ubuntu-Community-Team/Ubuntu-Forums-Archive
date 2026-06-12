---
title: "kernel compilation without internect connection"
date: 2005-04-11
forum: Installation &amp; Upgrades
---

### Post by RubenGonc on 2005-04-11
I want to recompile my kernel because I need to activate some options there to be able to use my usb modem. In this moment I don't have any internet connection, so I can't use the way demonstrated in the tuturials that use the apt-get system...

How can I recompile the kernel in this way? There are some tuturials for this?
thanks and sorry for my english   :roll:

---

### Post by fsman on 2005-04-11
[QUOTE=RubenGonc]I want to recompile my kernel because I need to activate some options there to be able to use my usb modem. In this moment I don't have any internet connection, so I can't use the way demonstrated in the tuturials that use the apt-get system...

How can I recompile the kernel in this way? There are some tuturials for this?
thanks and sorry for my english   :roll:[/QUOTE]
 I don't think that the kernel source is on the install CD. It may be on the DVD image - I'm downloading it now but it will take some time.

---

### Post by Xgates on 2005-04-11
Man I hope your good at kernels and then some, after 6 years in Linux, and have been compiling them since 2.0x I spent all day yesterday on it, and I still had 2 issues, at the end of the day. I've almost got it but a kernel recompile in Ubuntu is not nice, well that is if you want to strip it down to the bare essntials as I did, good luck

---

### Post by Xgates on 2005-04-11
Hmm the forum posted my first reply twice, hehe oh well this is just a EDIT of that, again good luck.

---

### Post by az on 2005-04-11
[QUOTE=Xgates]Man I hope your good at kernels and then some, after 6 years in Linux, and have been compiling them since 2.0x I spent all day yesterday on it, and I still had 2 issues, at the end of the day. I've almost got it but a kernel recompile in Ubuntu is not nice, well that is if you want to strip it down to the bare essntials as I did, good luck[/QUOTE]

sudo apt-get install linux-source-2.6 kernel-package libncurses-dev build-essential
cd /usr/src
sudo tar xvjf linux-source*
cd linux-source*
cp /boot/config-2.6.10.5 .config
sudo make menuconfig
configure until you are dizzy
sudo make-kpkg --revision=10 --append-to-version-mycusomkernel kernel_image kernel_headers

and you are done.

The only package not on your cd is the linux-source.  You can get it from packages.ubuntu.com and transfer it by usb stick, or something.

---

