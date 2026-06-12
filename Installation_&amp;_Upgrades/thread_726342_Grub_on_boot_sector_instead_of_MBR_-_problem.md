---
title: "Grub on boot sector instead of MBR - problem"
date: 2008-03-16
forum: Installation &amp; Upgrades
---

### Post by LinuxDev on 2008-03-16
Hi,

It's been a long time since I did not come here, I really like the "Here are the similar threads we found" feature, but unfortunately I didn't find what I wanted.

So, my configuration is:
Windows XP on 2 x SATA II in RAID0 + Ubuntu 7.10 on SATA I

To be able to boot on Linux, I don't want to play with raid software on Linux since I use a fake-raid (Intel ICH9R), but I saw that I could use the F12 bios menu to boot on my SATA I drive, where ubuntu is installed.

I first removed grub which was in the MBR by default, and which was giving error 21, and then I tried to modify it by booting again on the Ubuntu 7.10 CD and here is what I did:

```

sudo grub
root (hd2,6)
setup (hd2,6)

```

because Ubuntu is setup on the disk3 = hd2 = the SATA I one and on the 6th partiton of this hd2.

But I booted on the SATA I drive by using the F12 menu, but I still can't boot on my Ubuntu :( it gives an error like a problem in my boot.ini file.

So, my question is quite simple: do I need to set grub on the first partition of my hd2 ? which would be "setup (hd2,0)" to be able to boot on Ubuntu ? I think it's not working because partition (hd2,6) is not the main one, it's an extended one and it's not bootable but I might be wrong...please let me know what I should do, as I don't know if it is "safe" to set grub on (hd2,0) as it's a NTFS partition, and if it will fix the problem :)

Thanks ;)

---

### Post by louieb on 2008-03-16
Close - Grub counts partitions staring with zero too. So the 6th partition on the 3rd drive would be  (hd2,5).  When I put Grub in the boot sector I normally put in the partition that holds the / (root) file system. 

Kind of surprised the setup did not give some type of error. 
More here. [IDBS GRUB Page]("http://users.bigpond.net.au/hermanzone/p15.htm") and [IDBS WinGrub (NTLDR) and Ubuntu]("http://users.bigpond.net.au/hermanzone/p9.html")

---

### Post by LinuxDev on 2008-03-16
Hi,

Sorry, yes it's the right partition, number 6, and it's the 7th, yes, starting from 0 as well. But can't boot Ubuntu :(

As an alternative, if I boot on the setup CD, do you know which command I should use to load my installed Ubuntu ? my menu.lst is:

```


title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd2,6)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=b4431a69-fb0e-4c1e-9c28-499ca7a3ba4b ro quiet splash locale=fr_FR
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

```

and fdisk -l gives:

```

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sdc1   *           1        7649    61440561    7  HPFS/NTFS
/dev/sdc2            7650       20022    99386122+   f  W95 Etendu (LBA)
/dev/sdc5            7650       17473    78911248+   7  HPFS/NTFS
/dev/sdc6           17474       17735     2104483+  82  Linux swap / Solaris
/dev/sdc7           17736       20022    18370296   83  Linux

```

and:

```

grub> geometry (hd2)
drive 0x82: C/H/S = 20023/255/63, The number of sectors = 321672960, /dev/sdc
   Partition num: 0,  Filesystem type unknown, partition type 0x7
   Partition num: 4,  Filesystem type unknown, partition type 0x7
   Partition num: 5,  Filesystem type unknown, partition type 0x82
   Partition num: 6,  Filesystem type is ext2fs, partition type 0x83

```

Thanks, I really want "to Ubuntu", now :)

---

### Post by louieb on 2008-03-16
Don't think the Ubuntu live CD can boot an existing install. or guess I should say I've never done it.  But the  [Super Grub Disk]("http://forjamari.linex.org/projects/supergrub/") can. More on that from Herman's site:[IDBS on SuperGrub]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

You might try putting the Grub IPL in the mbr of sdc
```
root (hd2,6)
setup (hd2)
```

and use BIOS to boot to the 3rd drive. one problem is now sdc becomes sda so the root statement in your menu.lst is not right. 
A way to fix that is adjust the file /boot/grub/device.map 

Just how do you play to boot to Ubuntu. 
Change the boot order in BIOS?
or use the windows bootloader?
The reason I ask is the answer to getting Ubuntu to boot will be different depending on which drive is 1st in the boot order and what boot manager take control at boot.

---

### Post by LinuxDev on 2008-03-16
Hi,

Thank you but I got it working now.
As I said, to boot Ubuntu, I used the F12 boot menu, and select my SATA I drive. But the thing I had to change was, in my menu.lst:

```

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd2,6)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=b4431a69-fb0e-4c1e-9c28-499ca7a3ba4b ro quiet splash locale=fr_FR
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

```

by:

```

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=b4431a69-fb0e-4c1e-9c28-499ca7a3ba4b ro quiet splash locale=fr_FR
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

```

**(hd0,6)** because when I boot on my SATA I, it's seen as the first hard drive :) as you said ;)

so, to sum-up:grub installed on (hd2,6), but menu.lst with (hd0,6)

I'm so happy to get back to Linux.

Thanks

---

### Post by louieb on 2008-03-17
:guitar:Nice. Now one more thing to change. look for the line in menu.lst that has **groot= **in the automagic section. change (hd2,6) to (hd0,6) there also. 
**groot=** is what update-grub uses to build the root line when a new kernel is added.

---

### Post by LinuxDev on 2008-03-17
Hi louieb,

Yes, I noticed that after I installed all the updates (204 updates I think), I rebooted, but the menu.lst was back with the wrong hd2 instead of hd0 :)

I'll change to:

```

groot=(hd0,6)

```

cheers ;)

---

