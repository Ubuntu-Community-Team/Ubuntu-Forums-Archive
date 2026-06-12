---
title: "How to install grub on pen drive"
date: 2008-03-20
forum: Installation &amp; Upgrades
---

### Post by Balvinder25 on 2008-03-20
Hi all,

I would like to install Grub on a pen drive and not on the mbr of my hard drive.

I basically have 2 harddrives , one 160 gb and the other 40 gb.

Have reserved the first one for windows xp and the second for ubuntu 7.10

When installing ubuntu on the second hdd it automatically installed the boot loader on mbr of the first harddrive cause that was the primary.

I needed to know if its actually possible to install grub on a pen drive , so if i intend to use linux , i plug the pen drive in and select ubuntu , else it would boot straight into windows..

Any help would be really appreciated.

---

### Post by overdrank on 2008-03-20
> **Balvinder25 said:**
> Hi all,

I would like to install Grub on a pen drive and not on the mbr of my hard drive.

I basically have 2 harddrives , one 160 gb and the other 40 gb.

Have reserved the first one for windows xp and the second for ubuntu 7.10

When installing ubuntu on the second hdd it automatically installed the boot loader on mbr of the first harddrive cause that was the primary.

I needed to know if its actually possible to install grub on a pen drive , so if i intend to use linux , i plug the pen drive in and select ubuntu , else it would boot straight into windows..

Any help would be really appreciated.

Hi and this link may help
[https://help.ubuntu.com/community/BootFromUSB#head-5938e2f2bd2f35c1361bd9c633df4b954e5029cd](https://help.ubuntu.com/community/BootFromUSB#head-5938e2f2bd2f35c1361bd9c633df4b954e5029cd)
If you want to boot to windows first you could just edit you boot menu list
```
gksudo gedit /boot/grub/menu.lst
``` 
[http://users.bigpond.net.au/hermanzone/p15.htm#Fiesty_Fawns_new_menu.lst](http://users.bigpond.net.au/hermanzone/p15.htm#Fiesty_Fawns_new_menu.lst)

---

