---
title: "Ubuntu is missing"
date: 2010-06-04
forum: Installation &amp; Upgrades
---

### Post by SARAZIZ on 2010-06-04
Hi

I have used Window 7 , 32bit and installed Ubuntu as Independent system I mean it's alone on other partition and I Allocated
 for it 20GB , then I did clean install from Windows 7, 32bit 
to Windows 7 , 64bit after that I don't find Ubuntu , not on setup , not anywhere and still lose 17GB 
please help me 

* I'm sorry I'm Beginner in English and Harddisk problems

---

### Post by wojox on 2010-06-04
If you installed Windows after Ubuntu your boot loader got over written. Try reinstalling Grub2 [https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by darkod on 2010-06-05
Depending how you installed, it might not be independent as you think.
If you installed wubi inside windows, and it sounds to me like you did, even if the target partition is different from C:, wubi is still installed as a program inside windows. When you reinstall windows you need to reinstall all your other programs right? The same applies to wubi.

If you installed not only on separate partition, but on separate ext4 partition, on its own filesystem as full dual boot, then most probably just the grub2 bootloader on the MBR was overwritten and you need to reinstall it.

Which one did you do?

If you did the second, you can try booting with the ubuntu cd in live mode, and post the results of:

sudo fdisk -l (small L)

---

### Post by SARAZIZ on 2010-06-16
I installed ubuntu from CD 
and I don't want [COLOR=#000]Retrieval it , I need its space to extend volume [/COLOR]
[COLOR=#000][/COLOR] 
[COLOR=#000]sorry I late Because of exams[/COLOR]

---

### Post by darkod on 2010-06-16
> **SARAZIZ said:**
> I installed ubuntu from CD 
and I don't want [COLOR=#000000]Retrieval it , I need its space to extend volume [/COLOR]
 
[COLOR=#000000]sorry I late Because of exams[/COLOR]

If you want help provide the information from fdisk as I asked in my previous post.

You are asking us what to do but not providing information we need. How are we supposed to know what you have and tell you what to do?

---

### Post by maljaros on 2010-06-16
I have what seems to be the same problem described above by SARAZIZ. 
On a new computer with Windows7-Home pre-installed on a 500 Gig disk I installed Lucid Lynx from CD ISO.  The install process divided the disk into two roughly equal partitions with windows on the 1st and Lucid on the 2nd, both accessible under GRUB2 and both working perfectly.
The Windows section got messed when I tried to replace the pre-installed virus checker with another one recommended by my financial service provider.
I then used the Windows7 Recovery disk which did a reinstall of Windows7 on the 1st partition but the 2nd partition appears to have been wiped out.  Using the command *sudo fdisk -l* from a live CD boot gives me:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7450651f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       31211   250698758    7  HPFS/NTFS
ubuntu@ubuntu:~$ ^C

GParted (I have attached a screenshot - how do I embed this into the text?) shows the Lucid ext4 partition as unallocated space.  Does this mean that I have lost it (including some useful data) or can it still be resuscitated?

I hope I am not guilty of trying to hi-jack this thread.  
If so I do apologise.

Thanks MalJaros

---

