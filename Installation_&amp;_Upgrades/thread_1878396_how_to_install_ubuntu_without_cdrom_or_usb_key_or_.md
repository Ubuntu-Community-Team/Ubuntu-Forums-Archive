---
title: "how to install ubuntu without cdrom or usb key or external hard"
date: 2011-11-09
forum: Installation &amp; Upgrades
---

### Post by mohamedtoma73 on 2011-11-09
1-copy grldr and menu.lst into the root of c directory
2-write  the folowing  entry in boot.ini 
    c:\grldr="grub4dos
3-add xp entry in windows 7 boot menu using easybcd
4-in meu.lis add the following change the name of iso image according to the name of ubuntu release(the name in included menu.lst is ubuntu 11.10)
4-copy the downloaded  ubuntu iso image into the root of c partition
4-copy the contents of  ubuntu iso image into the root of c partition using ultraiso or any archive manager
5-resize your windows partition using disk utility of windows 7
6-create ntfs partition using  disk utility of windows 7
7-reboot  and choose xp ;then grub4dos and then install ubuntu from the menu
8-you cannot create or delete a partition using this method;but you can format  into  ext4 and change the mount point into / which is needed to install ubuntu
9-install ubuntu and is done

---

