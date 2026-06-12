---
title: "Partitions"
date: 2020-07-07
forum: Installation &amp; Upgrades
---

### Post by joeynaj on 2020-07-07
Hello i have the following issue:
I want to fully switch my desktop to Ubuntu and i do not know how to setup the partitions correctly.
I have 4 drives (2 128ssd's and 2 hdd 1tb and 3tb) i want have the following setup:
1 ssd to run / swap and efi partition
The 1 Tb hdd to be /home and other 2 drives to be loaded as folders in /home if possible.
Something goes wrong for me because i ended with duplicates folder names.
Can some one send me the correct configuration for sda sdb sdc sdd partitions?

Also i have tried to install it with legacy selected from bios and after I install it doesn't  post, why is that does it has to be efi?

Thank you

---

### Post by TheFu on 2020-07-07
Sounds like you only want 1 HDD connected during the install.  Then you can add the other storage where you like after the install.

Storage on Linux starts with a partition.  Next is either a volume manager or a file system. Sounds like you aren't interested in using a volume manager at all.  After the partition is created (use parted, gparted), then a file system should be created on that (use mkfs or gparted).  

That file system needs to be mounted where you want.  Any empty directory can be used as a "mount point." Well, really any directory can, but access to any files or subdirectories of that directory where the mount gets placed are unavailable post-mount.  The fstab is where mounts done at boot are configured.

Mounting other storage under a single userid's HOME is generally considered a bad idea, since backups need to be considered and if both HOME and that other storage are larger than the storage available for backups, a failure is likely - when it is too late.  To get around this, people will often mount extra storage elsewhere and create symbolic links from a directory in their HOME to that other location. For practical purposes, that is functionally the same result.

Here is my storage layout: [https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277](https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277)  I use LVM as a volume manager which means I can add storage where needed without any downtime.  Also, notice the sizes for each area.  The "LVs" can be logically considered "partitions", just much more flexible.  I happen to be using encrypted storage, but that isn't important. 

What is your plan for backups?  

Hopefully, this and the link above will give you some ideas. Be certain to read the other posts too. Lots of smart people here.

---

### Post by tea for one on 2020-07-07
I think that you need two devices connected during the installation.

128gb ssd
1tb hdd

**Remove** or **disable** the other two drives.

Ensure that all your data is **backed up** and **is restoreable**

Boot your usb live in UEFI mode.

During the installation process, choose something else for the partition editing.

Nominate your 128gb ssd for root / (the efi partition should be created automatically)
Nominate your 1tb hdd for /home

I would suggest that you use ext4 as a file system for both drives

You can format and add the other two drives subsequently.

---

### Post by oldfred on 2020-07-07
UEFI really should use gpt partitioning. But Ubuntu will let you use the now 35 year old MBR.
You can partition in advance with gparted or when installing, both require Something Else install option.
You can also use gparted but must change default partitioning first.
Select gpt under device, advanced over msdos(MBR) default partitioning before starting.

How you boot install media, is then how it installs, so you really want to boot Ubuntu live installer in UEFI boot mode.

Shows installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

New versions of Ubuntu use a 2GB swap file, so swap partition not required, although some (TheFu) like to have a bit larger swap like 4GB. Only if you want to hibernate (which is not recommended anyway) would you need a large swap about equal to RAM.

---

### Post by TheFu on 2020-07-07
> **oldfred said:**
> although some (TheFu) like to have a bit larger swap like 4GB.

There is a reason for that. ;)

On desktop installs with limited RAM - 4G and 2G, I'd have system crashes when the "modern browsers" would eat all the RAM and start into the swap.  With 2G swap, the crashes continued.  With 2G swap using zswap, the crashes continued.  But when I set swap to 4.1G, no more crashes and no crashes.  Perhaps it was all in my mind?  All I know is that 4.1G and Ubuntu desktops don't crash. Anything less and they do within 1 week.

For Ubuntu Servers, I try to have ZERO swap and just allocate RAM to each server as needed to handle peak requirements. Monitoring for a month gets me the data needed to set the max RAM allocation needed.

---

### Post by joeynaj on 2020-07-08
Thank you all for your help.

---

