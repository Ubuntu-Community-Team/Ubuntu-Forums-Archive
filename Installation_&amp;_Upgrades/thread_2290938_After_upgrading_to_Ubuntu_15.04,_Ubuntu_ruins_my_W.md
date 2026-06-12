---
title: "After upgrading to Ubuntu 15.04, Ubuntu ruins my Windows partition at every boot."
date: 2015-08-16
forum: Installation &amp; Upgrades
---

### Post by don40 on 2015-08-16
Hi,

I have multi-boot system with Windows 7 on one drive and Ubuntu on another. This was working fine until I upgraded from Ubuntu 14.10 to 15.04 about a week ago. Now, every time I boot Ubuntu from my hard drive, it writes 4 KB of apparently random data to the beginning of my Windows drive. The next time I try to boot Windows, I get error 0xc000000f: "The boot selection failed because a required device is inaccessible."

[http://i.imgur.com/qBOavPD.png](http://i.imgur.com/qBOavPD.png)

However, this doesn't happen when I boot Ubuntu 15.04 from a USB drive.

Here's the output of boot-info while everything is working (i.e., after I restored my Windows drive):
[http://paste.ubuntu.com/12100956/](http://paste.ubuntu.com/12100956/)

And here it is after booting Ubuntu, then rebooting from the login screen without ever logging in:
[http://paste.ubuntu.com/12101036/](http://paste.ubuntu.com/12101036/)

For reference, the drives listed in the boot-info output are:
/dev/sda1: 100MB Windows 7 system partition
/dev/sda2: Main Windows 7 partition

/dev/sdb1: An older Windows 7 partition that I rarely use anymore. It seems unaffected.
/dev/sdb2: Linux swap
/dev/sdb3: Main Ubuntu 15.04 partition

/dev/sdc1: ext4 storage drive

/dev/sdd1: Ubuntu 15.04 USB drive (FAT) that I used to generate the boot-info output.

/dev/sde1: Another USB drive (FAT) that I used for persistent storage while diagnosing the problem

You'll notice that in the first boot-info output, the /dev/sda2 hexdump shows a valid NTFS header, but in the second boot-info output, it says "Unknown bootloader on sda2" and the hexdump looks random.

I should probably mention that I have grub installed on /dev/sdb. Before I got my newer Windows 7 drive, I would dual boot between Windows 7 on /dev/sdb1 and Ubuntu on /dev/sdb3 (they weren't called "sdb" at the time, of course). Now I just use my BIOS's boot menu to choose between /dev/sda and /dev/sdb. When I select /dev/sdb, I get the grub menu, which has choices for Ubuntu and the older Windows 7 drive that I don't use much anymore.

I tried dumping the first 256 MB of /dev/sda to a file after restoring from a backup, and then again after reproducing the problem. When I compared the two files, there were over 4000 bytes that differed, and all of them were between bytes 105906176 and 105906176 + 4096. (105906176 being the beginning of /dev/sda2 at 101*1024*1024 bytes).

Then I booted Ubuntu a second time and dumped /dev/sda a third time to see if Ubuntu is writing the same 4 KB of data every time, and it's not. All three dumps were different in that same 4 KB block.

Does anyone know what would cause Ubuntu to write data to a Windows drive like this at boot? Thanks in advance!

---

### Post by oldfred on 2015-08-16
Boot-Repair is showing an issue, which often is from Windows left hibernated or needing chkdsk.
Much more common now with Windows 8 as its fast startup is really just hibernation.

Can you run testdisk on sda2. 
Testdisk can recover a NTFS partition boot sector from its backup, but before recovering it, it also has a compare (dump) function. 
       [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

I do not know how sda2's partition boot sector may get overwritten, unless you had a default location to reinstall grub into that partition set in your Ubuntu install. And grub did a major update. 

This should just show your sdb drive, not sda drive and partition in sda.

 #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc # for BIOS with grub-pc 
It will show drive model & serial number
to see drive info
sudo lshw -C Disk -short

---

### Post by don40 on 2015-08-16
Thanks, oldfred!

I figured it out, though. Ubuntu was trying to use my Windows drive as an encrypted swap drive. My /etc/crypttab set up a "cryptswap1" device on /dev/sda2, and my fstab mounted that device as swap space.

I don't know why upgrading to Ubuntu 15.04 triggered this. Maybe it changed the order of my drives so sda and sdb were different? Anyway, I didn't even realize I was using encrypted swap, so it didn't occur to me to check that when I upgraded.

---

### Post by Bucky Ball on 2015-08-17
Welcome. If fixed please mark as solved. See the first link in my signature. Good luck. ;)

---

