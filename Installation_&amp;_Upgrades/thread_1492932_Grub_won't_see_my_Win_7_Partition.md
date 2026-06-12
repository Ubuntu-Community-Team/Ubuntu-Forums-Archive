---
title: "Grub won't see my Win 7 Partition"
date: 2010-05-25
forum: Installation &amp; Upgrades
---

### Post by Kirky on 2010-05-25
Hey, Just installed 10.04, loving the new theme and default background.

My problem is that Grub won't detect my Win 7 boot. I installed it the way i normally do, seemed to work for the last few times.

I put in my Windows recovery disc to try and fix the MBR but that failed as the disc wont even see my Win 7 install. 
I have included my boot info script file.

Please help.

---

### Post by andru183 on 2010-05-25
howdy doody, could you type sudo fdisk -l to see if you drives there and let me know

if you dont see it by name maybe you'll know it by size

---

### Post by Kirky on 2010-05-25
lachlan@lachlan-desktop:~$ sudo fdisk -l
[sudo] password for lachlan: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008bfd4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9356    75143168   83  Linux
/dev/sda2            9356        9730     3005441    5  Extended
/dev/sda5            9356        9730     3005440   82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xdb56a6ac

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14594   117218304    7  HPFS/NTFS

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00043682

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121602   976761560    7  HPFS/NTFS
lachlan@lachlan-desktop:~$ 

There you go. Its the 120gb drive Win 7 is on.

---

### Post by darkod on 2010-05-25
You don't have any win7 boot files on your partition /dev/sdb1. Maybe it has that small boot partition created and you have deleted it. If it has the small partition, win7 keeps the boot files there.

Anyway, you could try the following:

1. Boot ubuntu and open Gparted (if you haven't installed it, you need to). Using Gparted set a boot flag on /dev/sdb1, your win7 partition.

2. Restart and go into BIOS. Set the win7 disk, the 120GB one, as first choice in the hdd order. Then boot with the win7 dvd and follow the instructions here to restore the boot files:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

You should need only the /fixboot command, no need to run the /fixmbr.

3. Restart and go again in BIOS, return the ubuntu disk as first option in hdd order. That should allow you to load ubuntu again. In ubuntu run:

sudo update-grub

and it should locate the restored win7 boot files now, provided all of the above worked.

PS. In the fdisk results you do have a boot flag on /dev/sdb1, so no need to do step 1. Strange, that boot flag was not in the results file.

---

### Post by andru183 on 2010-05-25
if you have gparted installed (if not type sudo apt-get gparted into terminal) open it from system>admin>gparted

click to old drop down arrow, select the drive /dev/sdb, click the coloured space with /dev/sdb writen on it and ask gparted to mount it in Partation>mount

sorry about the layout of my comments but i dont know how to put in code properly yet

---

### Post by Kirky on 2010-05-25
Umm, i tried that, typed in fixboot, came up with Element not found.

---

### Post by darkod on 2010-05-25
> **Kirky said:**
> Umm, i tried that, typed in fixboot, came up with Element not found.

I'm out of ideas then. That is a win7 issue, whether it can restore the boot files successfully. Grub2 is not detecting them simply because they are not there to be detected.
Try searching windows forums or tutorials for how to restore the boot files.

---

### Post by andru183 on 2010-05-25
try:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

looks long but helpful

---

### Post by andru183 on 2010-05-25
just after my last post i remembered this

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

last time windows 7 would boot for me this little program fixed it for me

let me know if it helps!!

---

### Post by Kirky on 2010-05-25
Ok, none of these worked, i need a program that can just install a Win7 Bootloader.

---

### Post by darkod on 2010-05-25
> **Kirky said:**
> Ok, none of these worked, i need a program that can just install a Win7 Bootloader.

Your win7 dvd. It should be able to handle that. You might need to run Repair This Computer routine few times, it seems to fix one bit at a time, but it should get you there at the end.

---

### Post by Kirky on 2010-05-26
The problem with that idea is that the Win7 DVD doesn't find my windows install at all.

---

### Post by darkod on 2010-05-26
> **Kirky said:**
> The problem with that idea is that the Win7 DVD doesn't find my windows install at all.

Some linux tools can help you install generic mbr on the disk but that would still need the correct win7 boot files to be in place so it can boot.
Only windows tools can help you restore your windows boot files. You're asking too much for linux to do that for you.

As I said earlier, try searching windows forums, and tutorials, google, for "win7 repair doesn't detect my system" or similar.

Not that we don't want to help, but I have never needed to use any special ways to restore the boot files, and I know only the standard procedure. It seems you need a more special approach, and after all this is a linux forum so people might have that in depth knowledge of windows repair process that you need.

PS. One option, if you are considering it, would be to use ubuntu or ubuntu in live mode and copy the files from the win7 partition that you need, and then reinstalling win7. But of course you would also need to reinstall all your software in it.

---

