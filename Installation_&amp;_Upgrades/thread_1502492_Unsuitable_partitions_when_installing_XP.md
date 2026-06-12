---
title: "Unsuitable partitions when installing XP"
date: 2010-06-05
forum: Installation &amp; Upgrades
---

### Post by s.v.z on 2010-06-05
Hi everyone! I`m running Lucid on my laptop. Now I wish to install WinXP in dual-boot mode, but it says there are no suitable partitions for it. The current state of my hdd is 

```

&#1044;&#1080;&#1089;&#1082; /dev/sda: 250.1 &#1043;&#1041;, 250059350016 &#1073;&#1072;&#1081;&#1090;
255 heads, 63 sectors/track, 30401 cylinders
Units = &#1094;&#1080;&#1083;&#1080;&#1085;&#1076;&#1088;&#1099; of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf90f73ae

&#1059;&#1089;&#1090;&#1088;-&#1074;&#1086; &#1047;&#1072;&#1075;&#1088;     &#1053;&#1072;&#1095;&#1072;&#1083;&#1086;       &#1050;&#1086;&#1085;&#1077;&#1094;       &#1041;&#1083;&#1086;&#1082;&#1080;   Id  &#1057;&#1080;&#1089;&#1090;&#1077;&#1084;&#1072;
/dev/sda1              20         498     3847567+  82  Linux &#1089;&#1074;&#1086;&#1087; / Solaris
/dev/sda2   *         499        5140    37286865   83  Linux
/dev/sda3            5141       30401   202908952    5  Extended
/dev/sda5            5141       18195   104864256    7  HPFS/NTFS
/dev/sda6           18196       27790    77071806    7  HPFS/NTFS
/dev/sda7           27791       30400    20964793+   e  W95 FAT16 (LBA)

```

I`ve tried to install it on existing ntfs partitions as well as to create a new partition with windows partition manager (the one that is offered in the beginning of the installation), /sda7 is the result, but it won`t help..

Any ideas?

---

### Post by oldfred on 2010-06-05
Windows only installs to primary partitions. sda1 thru sda4. You will have to delete or shrink sda5 and the extended partition and make a new NTFS partition sda4. Fortunately you still have one primary left. 

You will have to reinstall grub or grub2 after installing windows so make sure you have a liveCD to do that reinstall.

---

### Post by John Bean on 2010-06-05
XP won't install on an extended partition. It must be installed on the first primary partition if no other NT system is present but can be moved after installation and will continue to boot and run just fine. It's the installer rather than XP itself that imposes the limitations.

I run XP in a VM (VirtualBox) instead. Much simpler ;-)

---

### Post by s.v.z on 2010-06-05
Ah, so it's because of the extended partition. I'll try to move it with gparted now..

---

### Post by s.v.z on 2010-06-05
Gparted can't move the partitions.

```


ntfsresize -P -i -f -v /dev/sda5
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda5
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 107380994560 bytes (107381 MB)
Current device size: 85904824320 bytes (85905 MB)
ERROR: Current NTFS volume size is bigger than the device size!
Corrupt partition table or incorrect device partitioning?

```
 is there any other way to do it?

---

### Post by John Bean on 2010-06-05
And when you come to install it be aware that the XP installer can't cope with SATA disks (you'll get a BSOD after it loads the device drivers) so make sure your BIOS is set to use compatibility (PATA) disk mode if you're installing on modern hardware. 

And after it installs (perhaps that should be "if") it will have broken GRUB of course.

Go virtual, it keeps life simple ;-)

---

### Post by s.v.z on 2010-06-05
I know about SATA and Grub, thanks. The problem is that I can`t install it at all =)

---

### Post by John Bean on 2010-06-05
> **s.v.z said:**
> I know about SATA and Grub, thanks. The problem is that I can`t install it at all =)

Yep, installing XP second to Ubuntu isn't a bed of roses; been there, not going back :-(

My advice is to save your existing Ubuntu partition somewhere offline and repartition the disk from scratch, then install XP on the first primary partition. Ubuntu can then be copied back to its new location, fstab edited and GRUB installed from a live CD, job done.

Or have I mentioned going virtual? :-)

---

### Post by darkod on 2010-06-05
Be careful with trying too many things at once with partitioning tools. It usually leads to a disaster. Depending where you want to take the space from, you could do this (just an example):

Boot ubuntu cd in live mode, open Gparted.
Delete /dev/sda5, that will leave unallocated space inside /dev/sda3, the extended partition.
Shrink /dev/sda3 to the right but be careful to stop before you hit /dev/sda6.

That should leave the unallocated space outside /dev/sda3 now. Just create new ntfs primary partition and install XP there.

---

### Post by darkod on 2010-06-05
> **John Bean said:**
> XP won't install on an extended partition. It must be installed on the first primary partition 

Not necessarily on the first, only on primary is enough. Any primary will do.

---

### Post by John Bean on 2010-06-05
> **darkod said:**
> Not necessarily on the first, only on primary is enough. Any primary will do.

I won't argue, you may be right. But I've installed XP (literally) hundreds of times and there have been numerous instances of failure if a pre-existing non-NT OS was already installed on the first primary partition, yet installing in the first partition works every time.

From this experience I recommend installing the first copy of XP (or Win2k) to the first primary partition if there are other systems present, even though it may not be essential in any particular setup.

---

### Post by s.v.z on 2010-06-05
Well, in the end, I shrinked the swap partition, which was primary, installed there XP and used Acronis Partition Manager to clean up the mess. 
Lost /dev/sda5 while Gparting though. Will have to recover it later.

---

### Post by Arand on 2010-06-16
For the NTFS Error, this might be the problem:
[http://gparted-forum.surf4.info/viewtopic.php?id=13777](http://gparted-forum.surf4.info/viewtopic.php?id=13777)
And manual solution:
[http://gparted-forum.surf4.info/viewtopic.php?id=13937](http://gparted-forum.surf4.info/viewtopic.php?id=13937)

I had a very similar issue resizing a ntfs logical volume just now, and solved it by above tutorial.

- arand

---

