---
title: "Help: Accidentally installed Grub to my WindowsXP NTFS partition"
date: 2005-08-04
forum: Installation &amp; Upgrades
---

### Post by Hasbro35 on 2005-08-04
Scenario:
1. Re-installed Ubuntu to dual boot with Windows XP
    Partition 1: 25GB, NTFS, WindowsXP, C:\windows (primary partition)
    Partition 2: 30GB, FAT32, D:\ (primary logical partition as part of 55GB logical drive)
    Partition 3: 100 MB, FAT32, /boot (primary partition)
    Partition 4: 8GB, ReiserFS, / (logical partition as part of 55GB logical drive)
    Partition 5: 2.5GB, swap, swap (logical partition as part of 55GB logical drive)
    Partition 6: 14.5GB, XFS, /home (logical partition as part of 55GB logical drive)

2. I had Kubuntu 5.04 and Windows XP installed in a dual boot configuration.  Partition 3 did not exist originally.

3. I used Partition Magic to create Partition 3 at the front of the drive.  So the primary partition order is partition 3, partition1, partition2 (additionally with 4,5,6 all one logical drive) on the drive.  

4. Reinstalled Kubuntu so that GRUB would be installed to the new /boot partition.

5. When I got to the GRUB install portion I chose to _not_ install to the MBR and to install to a partition.

6. **Here's where I screwed up: I chose the wrong partition!**  Thought /boot was partition hda 0,0 (partition #1) when it was really hda 0,2 (partition #3).  I made the stupid assumption that if you put a partition at the beginning of a drive that it is tagged as the first partition.  *Just so you know, that is a bad assumption.*

7. So now my Windows XP NTFS partition is hosed due to GRUB installing to that partition.

8. I know the XP partition didn't get formatted, only that GRUB got installed there.  I guess Ubuntu can read/write to NTFS and that is why it was able to install there (or maybe this is an incorrect assumption).

9. Regardless, I can see all partitions when I run FIXBOOT from the Windows XP install CD; however, the NTFS partition does not read when I use another utility from the XP CD to auto-recognize OSes (not sure the name of the utility off-hand).

Question: How do I recover?  From other posts on the forum it looks like I might just be able to rescue the NTFS partition with Partition Magic...but before I take that drastic of a step I was wondering if there is a simpler fix.

Basically, in addition to "how do I recover?"  I was wondering "what does Ubuntu do when it tries to install GRUB to an NTFS partition that already has Windows installed on it?"

---

### Post by Hasbro35 on 2005-08-08
I have made some progress.  I was able to fix my NTFS partition using "testdisk".  This utility is great.  I suggest it to anyone that is having partition issues.  It is in "Universe" and is under the System Administration section.

Anyway, testdisk fixed my NTFS partition, but now I'm having an issue with Windows XP booting.  I re-installed GRUB using the Kubuntu install disk; however,  XP hangs when I try to load it.  I think the problem is that the boot.ini on the NTFS partition points to the wrong partition.

Here is the boot.ini:
> [boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn

and here is the results of fdisk -l:
> Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          14        3133    25061368+   7  HPFS/NTFS
/dev/hda2            3134        9964    54870007+   f  W95 Ext'd (LBA)
/dev/hda3               1          13      104391    6  FAT16
/dev/hda5            3134        7049    31455238+   b  W95 FAT32
/dev/hda6            7050        7441     3148708+  82  Linux swap / Solaris
/dev/hda7            7442        9399    15727603+  83  Linux
/dev/hda8            9400        9964     4538331   83  Linux

My thinking is that I made a mistake when I place the /boot partition prior to the Windows partition.  I have heard that Windows needs to have it's root partition (AKA C:\) on the first partition.  Anyway I'm going to try to change the boot.ini file and have it load Windows XP off the second partition and if that doesn't work then I'll using Partition Magic to move the /boot partition to the second partition on the hard drive.

---

### Post by dermotti on 2005-08-08
You could always pop in the win xp cd and run "repair mbr" from the recovery console.

---

### Post by jimmygoon on 2005-08-09
pop in the Win98 cd

boot to a command prompt

fdisk /mbr

or similiar ;)

---

### Post by Zyphrexi on 2006-07-31
I have a similar problem however I have no true winxp cd, the cd my comp came with is a pos re-ghoster from the generous folks at emachines. Is there anyway to fix this within linux?

---

### Post by Jimmey on 2007-09-07
Edit: ne'ermind ;-P

---

### Post by merlinus on 2007-09-07
> **Zyphrexi said:**
> I have a similar problem however I have no true winxp cd, the cd my comp came with is a pos re-ghoster from the generous folks at emachines. Is there anyway to fix this within linux?

Try supergrub:

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

More detailed info here:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

-merlin

---

