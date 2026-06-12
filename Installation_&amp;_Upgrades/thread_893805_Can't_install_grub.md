---
title: "Can't install grub"
date: 2008-08-18
forum: Installation &amp; Upgrades
---

### Post by iidestined on 2008-08-18
Hi. I wanted to dual boot ubuntu 8.04 with xp. I installed xp and installed ubuntu on a partition. The installation seemed to go well. I also have a 40gb slave. When I boot up, it goes straight to windows. So I booted up with the livecd and tried following some threads to reinstall grub with the
```

find /boot/grub/stage1 
```

command but it returns ```
Error 15: File not found
```

What am I doing wrong?

edit: windows is installed on sdb1 and ubuntu on sdb2 if that makes any difference.

---

### Post by linux_tech on 2008-08-18
help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows

Boot into the live Ubuntu cd. Open a terminal,
Start grub as root with the following command :  sudo grub

This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands

Code:
find /boot/grub/stage1

Using this information, set the root device:
Code:
root (hd?,?)
(i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Install grub 
Code:
setup (hd0)

exit grub 
Code:
quit

If, after installing grub, Windows will not boot you may need to edit /boot/grub/menu.lst

Open a terminal again and enter :
gksu gedit /boot/grub/menu.lst

---

### Post by logos34 on 2008-08-18
> **iidestined said:**
>  I also have a 40gb slave. 
edit: windows is installed on sdb1 and ubuntu on sdb2 if that makes any difference.

sounds like the slave is where windows and ubuntu is, and that's your boot drive, but maybe grub installed to the mbr of sda. (but then where'e stage1 file?)

post the output of 

sudo fdisk -l

Mount / (i.e. sdb2) -- what do you see in /boot/grub directory?

---

### Post by iidestined on 2008-08-18
> **linux_tech said:**
> help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows

Boot into the live Ubuntu cd. Open a terminal,
Start grub as root with the following command :  sudo grub

This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands

Code:
find /boot/grub/stage1

Using this information, set the root device:
Code:
root (hd?,?)
(i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Install grub 
Code:
setup (hd0)

exit grub 
Code:
quit

If, after installing grub, Windows will not boot you may need to edit /boot/grub/menu.lst

Open a terminal again and enter :
gksu gedit /boot/grub/menu.lst


I've tried that but like I've said, it can't find the file.

---

### Post by iidestined on 2008-08-18
> **logos34 said:**
> sounds like the slave is where windows and ubuntu is, and that's your boot drive, but maybe grub installed to the mbr of sda. (but then where'e stage1 file?)

post the output of 

sudo fdisk -l

Mount / (i.e. sdb2) -- what do you see in /boot/grub directory?

```
Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3da13da0

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3219f83d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2492    20016958+   7  HPFS/NTFS
/dev/sdb2            2493       19457   136271362+   5  Extended
/dev/sdb5            2493       19103   133427826   83  Linux
/dev/sdb6           19104       19457     2843473+  82  Linux swap / Solaris

```

it says there is no /boot/grub directory.

---

### Post by logos34 on 2008-08-19
your linux root is on a logical partition sdb5--not sdb2, which is the extended partition

> it says there is no /boot/grub directory.ok, try this from live cd:

>  sudo mkdir /media/sdb5
sudo mount -t ext3 /dev/sdb5 /media/sdb5
sudo grub-install --root-directory=/media/sdb5 /dev/sdb

reboot.  Hopefully grub menu screen will appear

---

