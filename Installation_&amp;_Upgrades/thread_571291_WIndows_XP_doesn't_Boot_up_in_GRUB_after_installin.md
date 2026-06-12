---
title: "WIndows XP doesn't Boot up in GRUB after installing Linux"
date: 2007-10-09
forum: Installation &amp; Upgrades
---

### Post by nowfal on 2007-10-09
Well as a Linux noob, here goes:

I installed linux from the LiveCD so I can dual boot with my existing Windows XP Home. SO I choose to resize IDE partition #1 and use freed space, everything went fine from here, ie Ubuntu 7.04 was installed.

Now after installing ubuntu, I restarted the computer, and on the GRUB boot loader, I choose WIndows XP home. The windows Xp boot up screen appears but after 2 seconds it restarts. I go back to booting up windows and it says windows have encountered a change in hardware of software and cannot open. I tried booting up in safe mode from that menu and that doesnt work either. Now I' m writing this message from Ubuntu itself, which seems to be working Ok and installing updates. 

Given the fact I'm new with linux, I hope its something I can sort out and its not permanent damage. I fear i might be needing a new installation of XP if I have messed things, up and I haven't got the Install disk for it!

---

### Post by Sef on 2007-10-09
Open the Terminal: Applications > Accessories > Terminal

then type this command:

```
sudo fdisk -l
```

Copy and paste what it says here.

---

### Post by nowfal on 2007-10-09
Here we go : 



Disk /dev/hda: 160.0 GB, 160041885696 bytes

255 heads, 63 sectors/track, 19457 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes



   Device Boot      Start         End      Blocks   Id  System

/dev/hda1   *           1        5751    46194876    c  W95 FAT32 (LBA)

/dev/hda2            5752       19079   107057160   83  Linux

/dev/hda3           19080       19457     3036285    5  Extended

/dev/hda5           19080       19457     3036253+  82  Linux swap / Solaris

---

### Post by emirazvy on 2007-10-11
I`ve installed linux and XP doesn`t boot anymore...it shows the advanced boot menu and boot screen for a few sec.then it reboots the system.......


Disk /dev/hda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         678     5446003+  83  Linux
/dev/hda2   *         679        7689    56315857+   7  HPFS/NTFS
/dev/hda3            7690       24321   133596540    f  W95 Ext'd (LBA)
/dev/hda5            7690       11515    30732313+   7  HPFS/NTFS
/dev/hda6           11516       16404    39270861    7  HPFS/NTFS
/dev/hda7           16405       23757    59062941    7  HPFS/NTFS
/dev/hda8           23758       24321     4530298+  82  Linux swap / Solaris

Disk /dev/hdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9196    73866838+   7  HPFS/NTFS
/dev/hdb2           14298       24321    80517780    f  W95 Ext'd (LBA)
/dev/hdb4            9197       14297    40973782+   7  HPFS/NTFS
/dev/hdb5           14298       18563    34266613+   7  HPFS/NTFS
/dev/hdb6           18564       24321    46251103+   7  HPFS/NTFS

Please HELP!!!!!!!!!!!!
how can i boot in xp?

---

