---
title: "Ubuntu/Windows 7 on seperate hard drvies."
date: 2012-04-06
forum: Installation &amp; Upgrades
---

### Post by mutualaff on 2012-04-06
Hello, I decided to try out Ubuntu. So I did some researching and came to the conclusion that I wanted to install Windows 7/Ubuntu on separate hard drives. So I dug out an old hard drive, unplugged the hard drive with Windows on it and installed Ubuntu 11.10 on the second hard drive. 

I found a tutorial about editing the /boot/grub/menu.lst file so that grub recognizes the Windows bootloader and lets me choose between the two. After I installed Ubuntu I attempted "sudo gedit /boot/grub/menu.lst" but there was no such file and it created a blank document. I added 

```
title Windows 7
root (hd1,0)
savedefault
makeactive
chainloader +1
```

to the menu.lst file, saved it and restarted as the tutorial stated. This did not work, and my computer directly booted into Ubuntu without giving me an option of choosing operating systems. 

The output of "sudo fdisk -l" is: 

```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2bd2c32a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       80324       40131   de  Dell Utility
/dev/sda2   *       81920    30801919    15360000    7  HPFS/NTFS/exFAT
/dev/sda3        30801920  1785229587   877213834    7  HPFS/NTFS/exFAT
/dev/sda4      1785231358  1953523711    84146177    5  Extended
/dev/sda5      1785231360  1946583039    80675840   83  Linux
/dev/sda6      1946585088  1953523711     3469312   82  Linux swap / Solaris

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00079b6c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   471638015   235817984   83  Linux
/dev/sdb2       471640062   488396799     8378369    5  Extended
/dev/sdb5       471640064   488396799     8378368   82  Linux swap / Solaris
```

The 1 terabyte hard drive is the one that contains the Windows installation, and the 250gb is the one that contains Ubuntu. The only way for me to "dual boot" is to physically change the position of the hard drives by switching up their connectors. 

I have tried changing the parameters of```
 root (hd1,0)
``` to (hd1,1), (hd1,2) etc. And I have tried (hd0,0) , (hd0,1) etc. 

I haven't been able to find any up to date tutorial on how to accomplish this, as they all state that modifying the menu.lst file will work.

Any help would be appreciated, thanks.

---

### Post by darkod on 2012-04-06
The tutorial you found is old, about grub1. Ubuntu since 9.10 uses grub2 which doesn't use menu.lst.

Boot ubuntu and delete the menu.lst you created. After that in terminal simply run:
sudo update-grub

That will detect all OSs and create entries in the boot menu.

You said you installed on separate disks. What are the linux partitions on /dev/sda?

Also, to boot grub2 from your ubuntu install you might need to change the boot priority in BIOS and use the 250GB disk before the 1TB disk.

---

### Post by mutualaff on 2012-04-06
Thanks. I am not sure what those Linux partitions are . I unplugged the 1TB drive when I installed Ubuntu, I don't recall installing anything before. Is there a way to reclaim those partitions? 

Would physically switching the hard drives be sufficient for giving the 250gb priority, or will I have to change the settings in the BIOS? I can boot into Windows/Ubuntu by switching the hard drives now.

---

### Post by mutualaff on 2012-04-06
I've got the dual booting working now, thanks for the help.

---

### Post by darkod on 2012-04-06
Well, it's up to you. I always prefer the BIOS way, but you might wanna use the motherboard Boot Menu during boot (all latest motherboards have them), or another approach.

Yes, you can reclaim those partitions. In windows open Disk Management, select them, and delete them one by one (if you are sure you have no important data there). Then simply create new ntfs partition from that space, or expand the last existing ntfs partition to take that space.

---

### Post by mutualaff on 2012-04-06
Thanks for the help.

---

