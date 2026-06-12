---
title: "Installation wizard does not forward to the next step"
date: 2007-10-24
forum: Installation &amp; Upgrades
---

### Post by jasperstroomer on 2007-10-24
Hello there!

I'm trying to install Ubuntu Desktop 7.10 on my pc but i've got a problem...

After booting from the live CD and starting the Install wizard all seams fine. The first 3 steps complete without any problems. When i click the Forward button at the screen where you select the keyboard language/settings a progress bar appears for a few seconds and disappears again. The Forward an Back button are disabled, and the wizard keeps displaying the keyboard settings page. 

It does not freeze, because I can still change the settings on the keyboard page. However I cannot continue the installation because the forward button is disabled.

I'm trying to install on an Asus P5B Deluxe motherboard (Intel ICH7R chipset). The SATA mode is set to RAID, but i'm the disk i'm trying to install onto is not part of any RAID array. 

The SATA is set to RAID because I was using 2 disks in RAID 0 when I installed Vista (using additional RAID drivers during Vista setup). When i set the SATA to IDE instead of RAID, Vista won't boot.

Does anyone recognize this problem, and more importantly, does anyone know how to fix it?

Thanks,

---

### Post by Pumalite on 2007-10-24
Post:
sudo fdisk -lu

---

### Post by KillaB7 on 2007-10-24
I'm also having major troubles getting partitions on my ICH7R fakeraid stripeset.
Been fighting for over 2 hours using the _[ FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)_ but keep running into errors trying to create my swap partition and/or keep being told I can only have one primary partition on the array and loosing all partitions.

Does anyone have a howto specifically for ICH7R FakeRaid?
Perhaps there's a problem with the version of GParted in Gutsy.  I'll go and try the aforementioned procedure with a Feisty CD.

---

### Post by Pumalite on 2007-10-24
Both of you guys should post the output of:
sudo fdisk -lu
(it's very difficult to help you without information)

---

### Post by KillaB7 on 2007-10-24
Here's mine.
Sorry I was at my parents house when I wrote my response earlier.

```

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sde: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Disk /dev/sde doesn't contain a valid partition table

Disk /dev/sdf: 0 MB, 327680 bytes
255 heads, 63 sectors/track, 0 cylinders, total 640 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdf doesn't contain a valid partition table

Disk /dev/sdg: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdg doesn't contain a valid partition table


ubuntu@ubuntu:~$ sudo dmraid -ay
ERROR: pdc: seeking device "/dev/sdf" to 18446744073709502976
ERROR: pdc: seeking device "/dev/sdf" to 18446744073709533696
ERROR: pdc: seeking device "/dev/sdf" to 18446744073709371904
ERROR: pdc: seeking device "/dev/sdf" to 18446744073709412864
ERROR: sil: seeking device "/dev/sdf" to 18446744073709354496
RAID set "isw_bjigefgffg_Volume0" already active


```

---

### Post by KillaB7 on 2007-10-24
And here's what happens after a write in fdisk:

```

Command (m for help): p

Disk /dev/mapper/isw_bjigefgffg_Volume0: 500.1 GB, 500113342464 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf2d965c7

                              Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_bjigefgffg_Volume0p1               1       60079   482584536   83  Linux
/dev/mapper/isw_bjigefgffg_Volume0p2           60080       60801     5799465   85  Linux extended
/dev/mapper/isw_bjigefgffg_Volume0p5           60080       60801     5799433+  82  Linux swap / Solaris

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 22: Invalid argument.
The kernel still uses the old table.
The new table will be used at the next reboot.
Syncing disks.

```

---

### Post by Pumalite on 2007-10-24
Well, your only solution is to stick to this: [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
Or get rid of your Raid Array (which I recommend)
Don't bother with Raids unless they are hardware.

---

### Post by KillaB7 on 2007-10-24
> **Pumalite said:**
> Well, your only solution is to stick to this: [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
Or get rid of your Raid Array (which I recommend)
Don't bother with Raids unless they are hardware.

Intel Storage Matrix is one of the fastest RAID0 implementations going (AFAIK).  Works great under XP.  Too bad it's such a pain to set up in Linux.

Oh well.  I guess I'll just go ahead and boot XP on one drive and Gutsy on another.  As long as NTFS support works well in Ubuntu and vise versa with Ext2fs I'll be happy, but I was really hoping for RAID0.  At least this way if one drive crashes, I can still boot into an OS.

---

### Post by Pumalite on 2007-10-24
I recommend you get an external hard drive and TrueImage XP to it. You can also backup your Gutsy to it and you'll still be wearing suspenders and a belt.

---

### Post by KillaB7 on 2007-10-24
I was so hung up on getting the ICH7R RAID going I forgot that my MB (ASUS P5W DH Deluxe) supports hardware RAID with a Silicon Image 4723!

My drives are now showing up as one....woohoo.

---

### Post by jasperstroomer on 2007-10-25
> **Pumalite said:**
> Both of you guys should post the output of:
sudo fdisk -lu
(it's very difficult to help you without information)


And here is mine:
= = = = = = = = = = START OF FDISK -LU = = = = = = = = = = 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   976768064   488384001    c  W95 FAT32 (LBA)

Disk /dev/sdb: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders, total 293046768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x28032802

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   293057729   146527841    7  HPFS/NTFS

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x316f316e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   625137344   312568641    7  HPFS/NTFS

Disk /dev/sdd: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1435059c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63   625137344   312568641    7  HPFS/NTFS

Disk /dev/sde: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders, total 240121728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6ac0d470

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1            2048   240117759   120057856    7  HPFS/NTFS

Disk /dev/sdf: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders, total 240121728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6ac0d471

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1            2048   240117759   120057856    7  HPFS/NTFS

= = = = = = = = = = END OF FDISK -LU = = = = = = = = = = 


I also added 3 screenshots (don't mind the color settings :-) )
Screenshot 1 shows the screen where i selected the keyboard layout
Screenshot 2 displays the progress bar i get after clicking Forward
Screenshot 3 shows the screen after the progress bar disappears.

---

