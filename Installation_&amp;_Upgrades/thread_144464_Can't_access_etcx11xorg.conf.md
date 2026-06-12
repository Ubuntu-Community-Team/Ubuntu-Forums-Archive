---
title: "Can't access /etc/x11/xorg.conf"
date: 2006-03-14
forum: Installation &amp; Upgrades
---

### Post by sharpie on 2006-03-14
Hi,

I'm totally new to Linux.

I've installed 5.10 to an old laptop that insisted that the desktop should load at 640x400 and gave me no options. After reading some threads I guessed it was set at 24 bit and to solve this I should edit /etc/x11/xorg.conf.

I think I followed all the instructions but whenever I opened /etc/x11/xorg.conf in gedit or nano it opened as a new file whether via the terminal window or the boot/recover option.

I finally solved it by using dpkg-reconfigure (again from a thread - thank you all) but why couldn't I access xorg.conf? What tiny but important thing am I missing?

Thanks.

---

### Post by Darkriser on 2006-03-14
try "sudo gedit /etc/X11/xorg.conf"

for further info, read this:

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by Gustav on 2006-03-14
it's a big x -- /etc/X11/xorg.conf

---

### Post by Darkriser on 2006-03-14
OH, just noticed, you are refering to x11 directory. but linux is CASE SENSITIVE - it means, you have to use X11 name, instead (copy and paste code in my previous post in terminal).

---

### Post by sharpie on 2006-03-14
There we are, I knew it'd be simple, case sensitivity.

Thank you guys, lesson learnt, first of many I suspect.

Sharpie

---

### Post by danlaptic on 2008-07-13
> **Darkriser said:**
> OH, just noticed, you are refering to x11 directory. but linux is CASE SENSITIVE - it means, you have to use X11 name, instead (copy and paste code in my previous post in terminal).

Of course it is!  Thank you.  Thank You!

---

