---
title: "Moving GRUB"
date: 2008-10-05
forum: Installation &amp; Upgrades
---

### Post by Spaceman9 on 2008-10-05
Is there a tool/GUI in Ubuntu that I can use to move GRUB? Or is the only way to use the CLI?

I need to chainload the Ubuntu GRUB so I need to move GRUB from the MBR to sdb1,something. I'm not sure if I need to move GRUB to sdb1,0 or sdb1,1. sdb is my second hard drive and that's what Ubunto is installed on. I installed Ubuntu with a / partition and a /home partition. Thankx for any help.

---

### Post by ajgreeny on 2008-10-05
You should be able to do it by moving grub to sdb with ```
sudo grub-install /dev/sdb
```Don't worry about the partition, just the device name.  Now restore your mbr with windows disk and set the bios to boot from sdb and you should be good to go.  Or have I read your question wrongly?

---

### Post by caljohnsmith on 2008-10-05
> **Spaceman9 said:**
> Is there a tool/GUI in Ubuntu that I can use to move GRUB? Or is the only way to use the CLI?

I need to chainload the Ubuntu GRUB so I need to move GRUB from the MBR to sdb1,something. I'm not sure if I need to move GRUB to sdb1,0 or sdb1,1. sdb is my second hard drive and that's what Ubunto is installed on. I installed Ubuntu with a / partition and a /home partition. Thankx for any help.
I don't know of a GUI tool, but installing Grub to the boot sector of a partition like sdb1 is really easy from the CLI; sdb1 would be (hd1,0) in Grub's World, so to install Grub to the boot sector of sdb1 and point Grub to sdb1 for its files (menu.lst, etc), just do:
```
sudo grub
grub> root (hd1,0)
grub> setup (hd1,0)
grub> quit
```
But what exactly are you trying to do? What boot loader are you going to use to chainload Grub? Also, it would help if you could post:
```
sudo fdisk -lu
```

---

### Post by Spaceman9 on 2008-10-05
ajgreeny thankx for your help. What I'm trying to do is a little different. I should have explanied that I guess. Sorry. See below.

caljohnsmith here's the fdisk thing. But it will all change with LFS.

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9d279d27

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    14538824     7269381   83  Linux
/dev/sda2        14538825    78156224    31808700    5  Extended
/dev/sda5        14538888    78156224    31808668+  83  Linux

Disk /dev/sdb: 40.9 GB, 40971829248 bytes
255 heads, 63 sectors/track, 4981 cylinders, total 80023104 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x90909090

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    16771859     8385898+  83  Linux
/dev/sdb2        16771860    80019764    31623952+   5  Extended
/dev/sdb5        16771923    80019764    31623921   83  Linux

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00063242

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   225215234   112607586   83  Linux
/dev/sdc2       225215235   234436544     4610655    5  Extended
/dev/sdc5       225215298   234436544     4610623+  82  Linux swap / Solaris

Ok, the reason I'm asking about chainloading is I have Ubuntu on my boot drive (sda) and Linux Mint on my second drive (sdb). 

I decided to try installing Linux From Scratch to learn more about Linux. So, the LFS book wants LFS installed to the boot drive (sda). So I need to format over Linux Mint and install Ubuntu on drive sdb. Then I can use sda for LFS and experience the limitless joys and rewards of compiling and stuff. Once I have LFS working I'll need to chainload Ubuntu. But, until LFS is working I can use StartUp-Manger to create a GRUB floppy of the Ubuntu GRUB and use that to boot up Ubuntu.

I was just thinking though since Ihave to install Ubuntu on drive sdb I could install GRUB on the sdb1,0 partition then Couldn't I. Can you tell I'm not very experienced at this? I hope installing LFS will give me a lot more knowledge. I have a lot to learn yet about Linux.

---

### Post by caljohnsmith on 2008-10-05
> **Spaceman9 said:**
> 
Ok, the reason I'm asking about chainloading is I have Ubuntu on my boot drive (sda) and Linux Mint on my second drive (sdb). 

I decided to try installing Linux From Scratch to learn more about Linux. So, the LFS book wants LFS installed to the boot drive (sda). So I need to format over Linux Mint and install Ubuntu on drive sdb. Then I can use sda for LFS and experience the limitless joys and rewards of compiling and stuff. Once I have LFS working I'll need to chainload Ubuntu. But, until LFS is working I can use StartUp-Manger to create a GRUB floppy of the Ubuntu GRUB and use that to boot up Ubuntu.

Can you simply change the boot order in your BIOS so that sdb boots before sda? If you can do that, you could maybe save yourself a lot of hassle moving your distros around on different drives; you could keep Ubuntu on sda and install LFS over Mint on sdb. Is changing the drive boot order in BIOS not an option for some reason? It seems like doing so would be your best option if I've understood your situation correctly.

---

### Post by Spaceman9 on 2008-10-05
I have problems just changing my soxs. I wouldn't really want to change BIOS. Between BIOS changing the order and the Ubuntu installer seeing them out of order most of the times I've installed it I wouldn't know what was what. Although, that's not unusuall for me. It's times like this that try mens programming skills, or something like that. 

Wouldn't changing the drives in BIOS confuse the UUID numbers in the Ubuntu fstab file? I think it would. If it did I'd have to edit the fstab file by hand and replace the UUID numbers with lables. I think I would anyway. I don't know for sure.

---

### Post by caljohnsmith on 2008-10-05
> **Spaceman9 said:**
> I have problems just changing my soxs. I wouldn't really want to change BIOS. Between BIOS changing the order and the Ubuntu installer seeing them out of order most of the times I've installed it I wouldn't know what was what. Although, that's not unusuall for me. It's times like this that try mens programming skills, or something like that. 

Wouldn't changing the drives in BIOS confuse the UUID numbers in the Ubuntu fstab file? I think it would. If it did I'd have to edit the fstab file by hand and replace the UUID numbers with lables. I think I would anyway. I don't know for sure.
Fortunately no, your UUIDs will not be changed by changing the BIOS boot order. Another idea is if you don't want to change your BIOS boot order, how about just leaving Ubuntu on sda, put LFS on sdb, and then let Ubuntu's Grub chainload your LFS installation, rather than the other way around like you mentioned? You can even use Ubuntu's Grub to chainload the sdb drive rather than the particular partition that LFS would get, so you don't need to worry about installing a boot loader in LFS's partition boot sector. What boot loader does LFS use anyway? Grub, LILO, or something else?

---

### Post by Spaceman9 on 2008-10-05
LFS uses GRUB but GRUB isn't installed untill the system is installed for LFS. Then I have to compile Gnome and then the software. I think I'll be installing LFS for the next year. It's like installing FreeBSD I guess.

---

