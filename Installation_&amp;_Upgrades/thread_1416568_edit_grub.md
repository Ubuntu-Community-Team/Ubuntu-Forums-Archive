---
title: "edit grub"
date: 2010-02-26
forum: Installation &amp; Upgrades
---

### Post by pmsik on 2010-02-26
In order to edit my grub in Ubuntu 9.10 I started a terminal window and did the usual thing such as "sodu gedit /boot/grub/menu.lst".
To my surprise a new window openend with no content at all.
Searching for the file "menu.lst" gave no result.
What is wrong here; the bootingmenu does exist as shown while booting.

---

### Post by tcchris on 2010-02-26
/etc/default/grub 
to start , there are posts on editing grub2

---

### Post by pmsik on 2010-02-26
I have looked in that map and still couldn't find any menu.lst.
I understand now that the 9.10 comes with a new Grub2. Didn.t realise that. Where can I find instructions for editing grub2 to make it possible to boot in a different OS.

---

### Post by oldfred on 2010-02-26
Some of the links I have saved. After any edit to any of the support files you have to run [COLOR=DarkRed]sudo update-grub[/COLOR] to get it to rewrite the grub.cfg file.

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
Herman's pages on Grub2
[http://members.iinet.net/~herman546/p20.html](http://members.iinet.net/~herman546/p20.html)
GRUB 2: A Guide for Users 
[http://kubuntuforums.net/forums/index.php?topic=3106368.0](http://kubuntuforums.net/forums/index.php?topic=3106368.0)

---

### Post by pmsik on 2010-02-26
Got it. Thanx boys.

---

