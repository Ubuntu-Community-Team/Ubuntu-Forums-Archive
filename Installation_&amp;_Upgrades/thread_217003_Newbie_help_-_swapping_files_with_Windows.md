---
title: "Newbie help - swapping files with Windows"
date: 2006-07-16
forum: Installation &amp; Upgrades
---

### Post by stopsatgreen on 2006-07-16
Hi,

Apologies if this has been answered before, I tried searching but couldn't find an answer that relates.

I have a dual-boot system, and my HD is partitioned in 4;

hdb1 : NTFS
hdb2 : FAT32 (Logical)
hdb3 : EXT3
Linux Swap Space

I want to be able to access hdb2 so I can swap files between Linux and XP; I used Norton Partition Magic to create all my partitions. XP reads hdb1 and hdb2, but Ubuntu only mounts hdb1.

In System > Admin > Disks I can see hdb2, but it tells me it's NTFS, not FAT32, and it won't let me reformat or get access to it. If anyone could help me out I'll be really happy.

I tried formatting hdb2 as both Primary and Logical and neither will let me access, reformat or mount it.

---

### Post by BuffaloX on 2006-07-16
Does XP recognize it as a fat32 partition?

In any case
Check/Fix it with Gparted.

To install gparted, Choose add/remove in menu applications.
Choose advanced and search for gparted.
Then Mark and apply.

The app is then found in your system/administration menu
as Gnome Partition editor.

---

### Post by stopsatgreen on 2006-07-16
After I format the drive in XP I can see it in Gparted; however, when I format to FAT32 in Gparted I get an error:

Error while formattting filesystem of /dev/hdb2

At least one operation was applied to a busy device.

In summary: in XP the drive is formatted, but when I enter Ubuntu, it isn't mounted. If I try to reformat in Gparted, I get an error and the partition resets to Unknown.

Update: I went back into XP and reformatted hdb2 as a FAT32 Primary Partition. Rebooted Ubuntu, opened Gparted and I see the partition /dev/hdb2, filesystem FAT32, but with the following error:

Unable to read the contents of this filesystem!
Because of this some operations may be unavailable.
Did you install the correct plugin for this filesystem?

The partition is flagged 'lba'. Does this make a difference? If so, how do I change it?

---

### Post by Choad on 2006-07-16
try 

$ sudo umount /dev/hdb2

before running gparted

---

### Post by stopsatgreen on 2006-07-16
I've got it working now! I tried reformatting in Gparted again, and this time it seemed to work. I mounted it temporarily in the command line, and then I could access it. Then, following the instructions [here]("http://ubuntuguide.org/wiki/Dapper#How_to_mount.2Funmount_Windows_partitions_.28FAT.29_manually.2C_and_allow_all_users_to_read.2Fwrite") I changed fstab and this time it mounted automatically on reboot.

Thanks for the help, which gave me a push in the right direction.

---

