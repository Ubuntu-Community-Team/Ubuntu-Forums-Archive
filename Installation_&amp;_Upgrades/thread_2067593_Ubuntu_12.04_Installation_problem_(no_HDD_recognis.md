---
title: "Ubuntu 12.04 Installation problem (no HDD recognised)"
date: 2012-10-07
forum: Installation &amp; Upgrades
---

### Post by chris2401 on 2012-10-07
Hey guys,

new user here. After using ubuntu for years on my laptop,i decided to install 12.04 on my desktop with windows 7.So first of all I re-installed my windows 7 and then i tried to install ubuntu. I have this problem in the installation type screen though - no HDD appears for ubuntu to be installed in:

[IMG]http://s15.postimage.org/6zrh2m6ff/Screenshot_from_2012_10_07_10_30_44.png[/IMG]


Yeah, so i googled the problem and i found that if you remove dmraid (sudo apt-get remove dmraid) the problem disappears. But that doesn't even help me! I remove dmraid , and still the same thing. I get the following 2 warnings though when removing dmraid:

```
cryptsetup: WARNING: failed to detect canonical device of overlayfs
cryptsetup: WARNING: could not determine root device from /etc/fstab

```I've also searched my BIOS settings,but couldn't do anything(my motherboard is an asus p7p55d-e and my HDD is an WD 320gb)! Any help PLEASEEEE? Thanks guys!

---

### Post by critin on 2012-10-07
Hi, Chris

I don't do crypting or raids, sorry.   These are your main issues.

As for ubuntu not seeing the hdd.  Have you looked through windows disk management to see what it sees in your disk?  Does it show up correctly there?

What did you do to prepare the space for ubuntu?  Have you created the partition yet?   I usually make a large extended, unallocated/free space partition,  formatting & sizing it in ubuntu during installation.

---

### Post by darkod on 2012-10-07
Wrong. You don't remove dmraid.

You used that disk in fakeraid earlier and it still has raid meta data remains on it, so the installer is ignoring it.
Removing dmraid makes it not see the meta data but it's still there.

Instead, use dmraid to remove the meta data and you can install ubuntu later:
sudo dmraid -Er /dev/sda

---

### Post by chris2401 on 2012-10-07
Thanks guys for the feedback!!

@critin : Everything is fine in windows . Disk management sees the partitions and the HDD healthy and everything,i have no problem.I created a 30gb partition for ubuntu and it didn't recognize it,either NTFS or exFat.

@darkod : I didn't know you could use dmraid like that. Thing is,  ubuntu won't recognize my HDD at all,not even with running fdisk , it only shows me the flash disk that's in my computer!

---

### Post by darkod on 2012-10-07
First, don't create any partitions for ubuntu from windows. It doesn't work on ntfs so those partitions are pointless. You will only use up primary partitions, and you might reach the limit. Delete that partition using windows Disk Management.

If even fdisk or parted don't show the disk, there is some problem with it. Sometimes windows ignores some errors and it might look like the disk is working fine, but linux doesn't and it will not show any partitions on it, especially if there is an error or corruption in the partition table.

What does fdisk and parted say exactly?
sudo fdisk -l (small L)
sudo parted -l

---

### Post by chris2401 on 2012-10-07
Here is what fdisk says:

```
Disk /dev/sda: 16.0 GB, 16039018496 bytes
255 heads, 63 sectors/track, 1949 cylinders, total 31326208 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    31326207    15662080    7  HPFS/NTFS/exFAT

```

and parted:

```
Model: JetFlash Transcend 16GB (scsi)
Disk /dev/sda: 16.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  16.0GB  16.0GB  primary  ntfs         boot

```

no HDD :(( i can't even find a way to fix any errors that can exist!

---

### Post by darkod on 2012-10-07
Sorry, I have no idea what is going on. Is the disk shown correctly in BIOS?

But if windows is working fine, it seems BIOS is detecting the disk OK.

If you have both sata2 and sata3 ports on the board, try the disk connected to another port.

---

### Post by chris2401 on 2012-10-07
Me neither, I'm suspecting my HDD has some kind of error that windows seems to skip but ubuntu doesn't , like you said. In BIOS the disk is detected normally.... I have only sata 3 connected but i'll try sata 2 and i'll let you know what happened.... I'll probably need to put another HDD in my computer though just to have ubuntu :/

---

### Post by darkod on 2012-10-07
One option is to use fixparts from live mode. Usually it can detect errors, if not too complicated, and repair them just by running the command. It would be like:
sudo fixparts /dev/sda

[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by chris2401 on 2012-10-07
Like I said earlier, i don't know how easy that is considering that  ubuntu won't even read my HDD at fdisk or parted. So it's hard to write  something instead of "sda" :)

---

### Post by darkod on 2012-10-07
You're right, I didn't think it through. :)

Don't know what more to suggest. It might be a good time starting to search for windows tools that verify partition table integrity and similar... It boots windows, you should be able to run some tool.

---

### Post by critin on 2012-10-07
When you booted into the live mode, did you take time to look at disk utility or gparted to look at the disk?   Does it only see the flash/cd?
I've had this issue of missing hdd a few times,  but don't remember how I solved it and that's not much help.  Unplugging and reseating the cables were among the things I did.  I found a bad cable once.  I know your disk can be seen in windows, but...

---

