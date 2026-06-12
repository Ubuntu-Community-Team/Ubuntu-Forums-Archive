---
title: "Dual Boot with Ubuntu 9.04 and Debian"
date: 2009-12-21
forum: Installation &amp; Upgrades
---

### Post by bm.riyadh on 2009-12-21
Hello,
Yesterday I have installed debian on my already running Windows & and Ubuntu 9.04 machine. The problem is, after installation only Debian and Win 7 boot option is available. I have reloaded grub and back my ubuntu. But, my debian gone! The same problem occurs when I installed OpenSUSE. I assume it is because of using same grub in ubuntu, debian and OpenSUSE. How can I can dual boot with two grub loader OS? Please help me. Thanks in advanced.

---

### Post by romeo.dejent on 2009-12-21
Hello,
You must use the chainloader option in your file "menu.lst". 

It is used for handing over to another boot loader.

---

### Post by oldfred on 2009-12-21
To chainboot you need to install grub to the partition that has debian. See #6 below.

chainboot 145 systems
[http://www.justlinux.com/forum/showthread.php?p=861282#post861282](http://www.justlinux.com/forum/showthread.php?p=861282#post861282)

Chainboot entry (title can be anything) drive x & partition y are where the grub is installed to the PBR.
title       Ubuntu 9.10 Karmic alpha/beta @ sdc7
root        (hdx,y)
chainloader +1

You also may be able to copy your menu.lst entry from the debian install into your menu.lst for ubuntu.

#reset grub boot
sudo grub
find /boot/grub/stage1 #you will get a response such as root (hd0,5)
root (hdx,y) #use the numbers from the previous command x is drive, y is partition
setup (hd0)
# Or
6. Type "setup (hd0,3)". This is key. Other instructions say to use "(hd0)", and that's fine if you want to write GRUB to the MBR. If you want to write it to your linux root partition, then you want the number after the comma, such as "(hd0,3)".
quit

---

