---
title: "Grub No such disk"
date: 2010-03-26
forum: Installation &amp; Upgrades
---

### Post by jimestesphl on 2010-03-26
Hello,
I'm running Windows 7 64 bit.  Installed Ubuntu 9.10 from cd.  Problem is that when I try to boot up I get:[INDENT]grub loading.
error: no such disk
grub rescue>
[/INDENT]I tried the find /boot/grub/stage1 but it did not find anything.  Right now I am running off of the Live CD and cannot boot into windows or ubuntu at startup.
I tried to install Ubuntu 9.10 again but got a message saying it was already installed.

I don't know what to do now.  Please help.

---

### Post by Cork87 on 2010-03-26
Install grub again and it should be solved.

---

### Post by Cork87 on 2010-03-26
[http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)

---

### Post by oldfred on 2010-03-27
Are you running the wubi version? If so you still want the windows boot loader in the MBR.

Fix for grub2 problem with wubi
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

---

