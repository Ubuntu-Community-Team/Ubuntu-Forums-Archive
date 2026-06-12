---
title: "Getting this message when choosing Windows 7 in GRUB"
date: 2015-09-11
forum: Installation &amp; Upgrades
---

### Post by KayeNg on 2015-09-11
error: no such device: CE0EBE6C0EBE4D69 
Setting partition type to 0x7 
Press any key to continue...

Everything boots fine including Windows 7, but I was wondering if it would worsen.  It didn't show that message before.  Does it have anything to do with me creating a primary fat32 partition for freedos (I have not installed freedos yet, just created a partition for it) ?

Again, everything boots ok, just wondering if I should be concerned with that.

Thanks!

---

### Post by oldfred on 2015-09-11
It was my understanding that Windows only booted from NTFS  partitions. 
Normal installs of Windows 7 or later use two partitions, a small Boot partition and the main install.
But then the Windows boot files need to be in a NTFS partition.
If creating a separate FAT32 primary partition that should be fine, but you get into the issue of boot flags.
Windows & DOS boot from MBR. MBR checks for partition with boot flag and jump to that partition to boot. So you cannot have boot flag on both Windows boot partition and your FreeDos partition. 
To install FreeDos you probably have to move boot flag to, then move back to Windows.

Grub does not use boot flag, it looks for boot files, so should be able to chain load to either even though boot flag is only on one of them.

---

### Post by yancek on 2015-09-11
The error message shows a windows partition UUID indicating it can't be found.  Usually with this message the system won't boot.  If you want to find out if there is a partition with that UUID, open a terminal and enter the command:  sudo blkid  Then check the output for the UUID.  You might look at the grub.cfg to see if the UUID is there.

---

### Post by KayeNg on 2015-09-12
Thanks guys!
yancek, I'm not sure I understand what you want me to do, but here's the output

/dev/sdc1: LABEL="MARLON" UUID="2E7B-BA02" TYPE="vfat" PARTUUID="0045ac08-01"
/dev/sda1: LABEL="Win7" UUID="9056153056151894" TYPE="ntfs" PARTUUID="9741cf47-01"
/dev/sda2: UUID="0AB7-F5BC" TYPE="vfat" PARTUUID="9741cf47-02"
/dev/sda5: LABEL="DATA" UUID="6BA4D79431264B29" TYPE="ntfs" PARTUUID="9741cf47-05"
/dev/sda6: UUID="a75287aa-4c7a-443d-8858-5b7604cfe2ce" TYPE="ext4" PARTUUID="9741cf47-06"
/dev/sda7: UUID="5bf83df1-edf5-4bb3-b51b-616a42e63459" TYPE="swap" PARTUUID="9741cf47-07"
/dev/sdb1: LABEL="Old_Disk" UUID="E8BAEDF6BAEDC0E4" TYPE="ntfs" PARTUUID="b3b6bfe0-01"

I wonder if I should proceed with installing freedos because of this....good thing I checked with you guys first, don't want to mess up the system and do it all over again.

UPDATE:  The message doesn't appear anymore.  Now I'm wondering if it has something to do with me formatting the fat32 partition using GParted while on Lubuntu.

---

### Post by yancek on 2015-09-12
In your original post, you indicated that when you booted you got this message:

> error: no such device: CE0EBE6C0EBE4D69 

The number/letter combination is the UUID for a specific partition.  That partition doesn't exist so either it was deleted or the UUID was changed.  Another possibility would be if you had a partition on an external drive with an entry in the fstab file for it and that drive was not attached.  If you don't get the message any longer, nothing to worry about.  I've never used Freedos and don't know anything about it.  I believe it does need to be installed on a primary drive, or at least like windows, needs its boot files on a primary.

---

### Post by KayeNg on 2015-09-13
Alright, thanks a lot!

---

