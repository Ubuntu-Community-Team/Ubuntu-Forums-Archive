---
title: "Blank Screen after installation ubuntu 7.10"
date: 2008-02-01
forum: Installation &amp; Upgrades
---

### Post by konohamarusan on 2008-02-01
Hi,
I have installed ubuntu to my dell 1400 vostro, with nvidia 8400 graphics card. I installed it on an external hard drive. I installed ubuntu 7.10 by using the alternate cd. (the other cd  freezes during the installation at 15%)
After installing, I reboot the system and the system goes blank. 
After that, I tried to boot the system in recovery mode, but I got the following error:


filesystem type is fat, partition type 0xde

kernel /boot/vmlinuz-2/6/22-14-generiz rood=UUID=28de5afa-c368-4d9c-bd8c-42c54
c4bbbcb ro single

Error 17: file not found

Press any key to continue..._

Any suggestions?

---

### Post by taurus on 2008-02-01
Installing Ubuntu on a fat filesystem is a real bad idea.  You need to reinstall Ubuntu but this time, install it on it native filesystem, ext3.

---

### Post by konohamarusan on 2008-02-01
Installing Ubuntu on a fat filesystem is a real bad idea. You need to reinstall Ubuntu but this time, install it on it native filesystem, ext3.

I am very new to linux, and it is my first attemp to install it :(
I have created two ntfs partitions for ubuntu before installing it. One for ext3 and one for the swap space. I don't understand what you meant to install it on a native filesystem? How can I do that?

Thanks!

---

### Post by PmDematagoda on 2008-02-01
There are many native file systems on which Ubuntu can be instaled on:-
ext3
ext2
JFS
ReiserFS
XFS

There may be more.

Now if you want Ubuntu to set itself up automatically(which is recommended if you are unsure of what you should do), then just select the choice of allowing Ubuntu to use a percentage of the hard disk or by telling it to use one entire hard disk in the Partitioning part of the install.

---

### Post by konohamarusan on 2008-02-01
I chose the option that Ubuntu sets its partitions automatically and re-installed it again. The errors are the same as the previous one. 
Any more suggestions, please?

---

### Post by taurus on 2008-02-01
So, you installed it on your harddrive but you can't boot now?  Can you boot into the LiveCD and post the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```
Not sure whether you copied/pasted it wrong but there was a typo with an entry in /boot/grub/menu.lst.

```

kernel /boot/vmlinuz-2.6.22-14-generic **[COLOR="Blue"]rood[/COLOR]**=UUID=28de5afa-c368-4d9c-bd8c-42c54c4bbbcb ro single
```
That should be **_root_**.

---

### Post by konohamarusan on 2008-02-02
Thanks for your reply.

I boot from the cd at the safe graphics more and have done the following which doesn't mean anything to me :( DO you think I am doing something wrong here?

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          10       80293+  de  Dell Utility
/dev/sda2              11        1316    10485760    7  HPFS/NTFS
/dev/sda3   *        1316        6538    41943040    7  HPFS/NTFS
/dev/sda4            6538       14594    64709632    f  W95 Ext'd (LBA)
/dev/sda5            6538       14594    64708608    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0e9a630b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       11856    95232000   83  Linux
/dev/sdb2           11856       12752     7193600   82  Linux swap / Solaris
/dev/sdb3           12752       14027    10240000    7  HPFS/NTFS
/dev/sdb4           14028       60801   375712155    5  Extended
/dev/sdb5           14028       23753    78124063+  83  Linux
/dev/sdb6           60050       60801     6040408+  82  Linux swap / Solaris
/dev/sdb7   *       23754       59297   285507148+  83  Linux
/dev/sdb8           59298       60049     6040408+  82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by konohamarusan on 2008-02-02
Also the rood thing is a typo, i looked at the file and see that it is in fact root as you said.

---

### Post by lnk5700 on 2008-02-02
> **konohamarusan said:**
> Hi,
I have installed ubuntu to my dell 1400 vostro, with nvidia 8400 graphics card. I installed it on an external hard drive. I installed ubuntu 7.10 by using the alternate cd. (the other cd  freezes during the installation at 15%)
After installing, I reboot the system and the system goes blank. 
After that, I tried to boot the system in recovery mode, but I got the following error:


filesystem type is fat, partition type 0xde

kernel /boot/vmlinuz-2/6/22-14-generiz rood=UUID=28de5afa-c368-4d9c-bd8c-42c54
c4bbbcb ro single

Error 17: file not found

Press any key to continue..._

Any suggestions?

i have the same problem!!:(

---

