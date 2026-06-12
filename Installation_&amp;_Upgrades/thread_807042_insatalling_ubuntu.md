---
title: "insatalling ubuntu"
date: 2008-05-25
forum: Installation &amp; Upgrades
---

### Post by piojo7 on 2008-05-25
hello,

if I install ubuntu on a different hard disk (on the other there's windows) ,
can I do a boot loader when the computer starts? and if I do, how?

thanks

---

### Post by Pumalite on 2008-05-25
Boot your Live CD and post:
sudo fdisk -l
Probably there are no problems.

---

### Post by piojo7 on 2008-05-25
> **Pumalite said:**
> Boot your Live CD and post:
sudo fdisk -l
Probably there are no problems.

do you mean to boot before installation?

---

### Post by Pumalite on 2008-05-25
You will need to boot the Live CD to post that command from the Terminal. It will not install.

---

### Post by piojo7 on 2008-05-25
> **Pumalite said:**
> You will need to boot the Live CD to post that command from the Terminal. It will not install.
ok. what do I do afterwards? 
install normally?

---

### Post by Pumalite on 2008-05-25
Post the output of the command first.

---

### Post by piojo7 on 2008-05-31
> **Pumalite said:**
> Post the output of the command first.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x06fd06fd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3602    28933033+   7  HPFS/NTFS
/dev/sda2            3603        9733    49247257+   f  W95 Ext'd (LBA)
/dev/sda5            3603        9733    49247226    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa285a285

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/sdb2            6375       30400   192988845    f  W95 Ext'd (LBA)
/dev/sdb5            6375       30400   192988813+   7  HPFS/NTFS

---

### Post by piojo7 on 2008-05-31
I'm sorry 4 the big delay. I had some trouble with the hard disk..

---

### Post by Pumalite on 2008-05-31
You have a limit of 4 primary partitions per drive. Are you using Vista or XP?

---

### Post by piojo7 on 2008-05-31
xp.
is that a problem?

---

### Post by Pumalite on 2008-05-31
Vista would have been more of a problem. With XP< you can use Gparted and shrink XP. Allocate at least 20 GB to Ubuntu. You can further partition that space into 3 -New- partitions. You have to create an extended partition and within that make 2 -New- partitions:
19 GB for -/- and 1 GB for /swap (/swap equals RAM in laptops)
Adjust as neccessary.

---

### Post by piojo7 on 2008-05-31
i dont understand.

why i need to do all this? I want to install on a different hard disk (i dont need 2 partitions on that one)

---

### Post by Pumalite on 2008-05-31
You can chose the drive, but if you want to be sure of what you are doing; at least go Manual during the installation and choose where to plant your Ubuntu.

---

### Post by piojo7 on 2008-05-31
ok. but the dual boot will work?
is there something special i need to do for it?

---

### Post by Pumalite on 2008-05-31
Ubuntu installs Grub to the MBR by default and that gives you a menu with dual boot. I hope you have both IDE or both SATA.

---

