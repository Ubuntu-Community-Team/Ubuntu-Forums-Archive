---
title: "installing Ubuntu 8.4 and Red Hat Enterprise Linux 5"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by htabesh on 2008-04-29
Hello Everybody...

I have an IDE (250 GB) hard disk, I have installed Red Hat Enterprise Linux 5 on my system with 3 partition:
1: Boot 200MB
2. /    30GB
3. SWAP 2GB

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000253e7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          25      200781   83  Linux
/dev/sda2              26        3849    30716280   83  Linux
/dev/sda3            3850        4104     2048287+  82  Linux swap / Solaris
/dev/sda4            4105        6536    19535040    5  Extended
/dev/sda5            4105        6536    19535008+  83  Linux
```

then I have got a copy of my "vmlinuz-2.6.18-8.el5" and "initrd-2.6.18-8.el5.img" in the "Boot" partition and then installed Ubuntu 8.4, and copied that 2 file to the Ubuntu's "Boot" partition, and Edited my "menu.lst" in the way below : 

title		Ubuntu 8.04
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=94f16ac5-71f5-4c18-882e-a54a5a03cc15 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Red Hat Enterprise Linux 5
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.18-8.el5 ro root=LABEL=/1 rhgb quiet
initrd		/boot/initrd-2.6.18-8.el5.img

but I can't Dual boot them, Please help me.

---

### Post by PmDematagoda on 2008-04-29
What error do you get(if any)?

---

### Post by htabesh on 2008-04-29
Ummm...
When I reboot my system, I couldn't boot Red Hat, Grub wants me to "Press any key to contiunu" and then back to the GRUB list.

---

