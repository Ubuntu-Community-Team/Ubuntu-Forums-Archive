---
title: "Installation from 1st primary partition"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by Mohammed Abbas on 2006-10-28
[SIZE=2]Hi folks ,

I've successfully done all steps mentioned in this document :

[https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows)

and used ;
[/SIZE]```
 title Install Ubuntu
kernel   (hd0,0)/ubuntu/install/vmlinuz root=/dev/ram0 devfs=mount,dall ramdisk_size=17000
initrd   (hd0,0)/ubuntu/install/initrd.gz
```[SIZE=2]

[/SIZE]      [FONT=Tahoma][SIZE=2]for Edgy , right ?


The problem is , when installation comes to hardware detection it asks to insert the installation CD , hence I couldn't go through any more ..

What shall I do then to maintain boot from hd , if this could be ?

Regards,
Mohammed Abbas[/SIZE][/FONT]

---

### Post by Mohammed Abbas on 2006-10-28
I have to say I did the netboot appraoch and it worked fine :-D , ... the installer connected to us.archives.ubuntu.com . I've canceled when it reached HD partitioning step .

But , how could I know the installation will go for Edgy ?
and , will my 1st primary partition be affected except the installation of GRUB in the End ?

I still want dual boot Ubuntu + Windows XP

Regards,
Mohammed Abbas

---

