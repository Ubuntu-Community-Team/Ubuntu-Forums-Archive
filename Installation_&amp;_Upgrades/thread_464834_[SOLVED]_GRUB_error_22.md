---
title: "[SOLVED] GRUB error 22"
date: 2007-06-05
forum: Installation &amp; Upgrades
---

### Post by opossumjack on 2007-06-05
Help me please!!!!!!

GRUB stopped working today...

with a error22....

I think I should reinstall GRUB from the Ubuntu live CD...

How can I do?
I don't have any permission to write on my hard disk....

Help....:( please...

thanks in advance

---

### Post by Herman on 2007-06-05
Hello opossumjack,
Grub just stopped working? 
Try reading this link and see if it helps you figure out your own problem, [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#22](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#22)

If you need more specific help you will need to at least post the output from sudo fdisk -lu or a screencap of you partitions from GParted here please, along with a copy of the bottom part of your /boot/grub/menu.lst file.  Most of the time someone will be able to help you if they can see those files.
```
sudo fdisk -lu
``````
sudo gedit /boot/grub/menu.lst
```

This link should help you mount your Ubuntu system in a Ubuntu Live CD and gain access to certian vital files with permission to edit them to rescue your system. [                                  Mount a Ubuntu ext3 or reiserfs filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD") rescue your Linux system with a Live CD[COLOR=#666666][/COLOR]

Regards, Herman

---

### Post by opossumjack on 2007-06-20
Thanks a lot... it works now!!!!!

I think it's a hard disk problem... My boot HD is gonna die... I think I should change it... :D


Thanks

---

