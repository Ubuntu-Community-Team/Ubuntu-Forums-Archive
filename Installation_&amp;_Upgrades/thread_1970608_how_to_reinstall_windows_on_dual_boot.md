---
title: "how to reinstall windows on dual boot"
date: 2012-05-01
forum: Installation &amp; Upgrades
---

### Post by qqww on 2012-05-01
Hello

I need to reinstal my windows

in Ubuntu  i have a windows fold

is that the correct set up to reinstall my windows

i also read where after windows reinstall i will have to go back and do something with  GRUB  whatever grub is ???????


thanks

---

### Post by darkod on 2012-05-01
When you say you have a windows folder you probably mean you are mounting your windows partition.

Simply boot with your windows cd and install it where you want. You might need to redo the mounting setup in ubuntu depending how it was done.

Yes, windows will overwrite the grub2 bootloader on the MBR. You will have to boot with the ubuntu cd in live mode and reinstall it. You have the instructions here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Grub2 is the ubuntu bootloader which boots the OSs.

---

