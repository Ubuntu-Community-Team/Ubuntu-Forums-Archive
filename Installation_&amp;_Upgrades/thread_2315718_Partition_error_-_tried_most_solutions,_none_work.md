---
title: "Partition error - tried most solutions, none work"
date: 2016-03-01
forum: Installation &amp; Upgrades
---

### Post by jeremy68 on 2016-03-01
Hey, all. I'd like to thank you in advance for reading this, even if you cannot offer appropriate assistance. Unfortunately I have no screenshots due to the trouble I'm experiencing.

I recently decided to install Xubuntu as a dual-boot option on my HDD. After attempting to partition the remaining free space on it (a free space ~900gb) from the Xubuntu installer, the installer returned error code 141 after trying to create the 1st ext4 partition (Not sure if this is relevant but I created three: Two primary partitions and a swap space. After trying to boot back into Windows so I could research this error, the message "Reboot and select proper boot device" appeared and it seemed, at the time, as if Windows was not going to boot. I had attributed this to a hypothetical terminal problem with the HDD; for some time before this I was hearing clicks and various other noises coming from the HDD. I purchased a new WD Blue 1 terabyte and installed it.

I ran the Xubuntu installer once again, and received the same error in terms of the creation of the partition. I decided to run Xubuntu from the thumbdrive and possibly use gparted to sort the issue out (with the new HDD) and I see the entire hard drive was unassigned; the exclamation point denoting a warning was also showing. The error, according to gparted, was that the disk label was unrecognized. Trying to create a new partition table, the gparted informed that there was residual GPT data on the hard disk; I knew this was impossible being that the drive was new but nevertheless I ran gdisk to erase any gpt data "present" on the hard disk. Thinking the problem was solved, I ran gparted again and . . . found the same error. Same problem with the warning symbol (unrecognized disk label), and the attempt to create a partition table shows that the ghost gpt data still exists. If I ignore both of these and try to create partitions anyway, none of the partitions are created; the error given is "unrecognized disk label". I can attempt to create the label myself using mklabel following various instructions online but to no avail. 

I seem to have tried everything; it must be something I am doing, no? I appreciate any help given.

---

### Post by Bucky Ball on 2016-03-01
*Thread moved to **Installation & Upgrades**.*

Which version of Windows are you using? Your problem could be related to UEFI.

How did you create the partitions to install Ubuntu to? What filesystem are they? Is there any free space left on the drive?

In Gparted on the new drive, go 'Actions' (I think but you'll find it) then choose 'create partition table'. This will get rid of the exclaimation mark. Then create your partitions and make them EXT4 and a swapspace (I use 'Something Else' during install and do it then personally).

Hope that gives some clues.

---

### Post by jeremy68 on 2016-03-01
Well, I was using windows 8 on the old hdd but this is a completely new hard drive. I used the "other" option to create the partitions myself as opposed to using the entire disk. What you've advised I've done repeatedly (noted in first post) and it never works; it always reverts back to the original state, which is 1. The exclamation point detailing the unrecognized disk label and 2. The presence of gpt data even though I've deleted it using gdisk and it's a brand new HDD.

running fdisk -l gives this output (I'll try to paraphrase being that I'm on a phone)

/dev/sda: 1000.2 GB
255 heads, 63 sectors/track, 121601 cylinders, 1953525168 sectors 
Units = sectors of 1 * 512 = 512 bytes
Sector size= 512 bytes / 4096 bytes
I/O size 4096 bytes / 4096 bytes
Disk identifier: 0xffffffff 

dev/sda doesn't contain a valid partition table (even after multiple attempts)

---

### Post by oldfred on 2016-03-02
Did you use Windows to change from gpt to MBR?
Windows does not correctly convert a drive and leaves the backup gpt partition table. Then Linux tools see both MBR & gpt and do not know what you have and pretty much assume you want to totally repartition to resolve error.

If you really want the 35 year old MBR(msdos).
       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
sudo fixparts /dev/sda 

Windows only boots in BIOS mode from MBR, so if installing Windows to drive you may need MBR.
Ubuntu can boot in BIOS or UEFI from gpt partitioned drives.

      
 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)

---

### Post by jeremy68 on 2016-03-14
Solved the issue.

I changed the port where the SATA cable would connect with the motherboard. Must have been faulty. Connected to a new slot, all problems have disappeared. Thank you for your advice, though,

---

### Post by Bucky Ball on 2016-03-14
Good news. Please mark thread as solved. See first link in my signature below for how.

---

