---
title: "Win 8.1 + Ubuntu - Win 8.1 Automatic repair"
date: 2015-07-07
forum: Installation &amp; Upgrades
---

### Post by Raghu_Bulusu on 2015-07-07
I have a  dual boot setup Ubuntu 14.04 + Win 8.1. Recently Ubuntu pushed some updates and after updating I am having issues booting into Win 8.1. I get automatic repair screen and it loops. Here is my boot info from Boot repair. Boot repair didn't help.

[http://paste.ubuntu.com/11834325/](http://paste.ubuntu.com/11834325/)

---

### Post by oldfred on 2015-07-07
Do not run Boot-Repair's auto fix. That just installs grub every where.

Grub only boots working Windows. So I doubt that an Ubuntu update caused issues, unless drive number of Windows was seen as a different drive. If I add a flash drive to my system it is sde, but when I reboot it is sdb and I have to manually edit set root commands in grub if I want to boot something not using UUIDs.

I would install Windows boot loader to your sdd or Windows drive. Then you can directly boot it from BIOS. After Windows is working change boot back to Ubuntu drive or sdb.

I might change port order of drives and make Windows sda. With my system drives were in SATA port order. 

But boot drive is always hd0 from BIOS when booting. And that may even be part of what Windows is complaining about. The drivemap command in grub is to reset BIOS boot order, so Windows sees it as it should if it booted itself.

---

