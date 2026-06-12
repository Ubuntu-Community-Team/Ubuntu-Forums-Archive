---
title: "Dual Boot Killed by Windows Repair"
date: 2016-09-13
forum: Installation &amp; Upgrades
---

### Post by gde061-www on 2016-09-13
As the title says, I had Win 7 Pro and Ubuntu 14.04 peacefully coexisting on my home PC, along with a third partition (Fat32) for transferring files from Ubuntu to Windows.  

Windows had a fatal crash recently.  Prior to Windows Repair, I could still boot up Ubuntu no problem".  But the first time I tried booting into Windows, after the boot menu, I got a black screen recommending to let windows repair fix my system.  Which I unfortunately did.    This neither fixed windows, or respected the dual boot.  

After the Windows Repair, nothing will boot.

I ran ubutu boot repair. It also failed.  

The boot info file is here:  [http://paste.ubuntu.com/23174329/](http://paste.ubuntu.com/23174329/)

Please help me figure out how to get this running again.  Thanks in advance.

---

### Post by oldfred on 2016-09-13
Grub only boots working Windows.

You may need to temporarily reinstall Windows boot loader with your Windows repair flash drive or a Windows type boot loader with Boot-Repair's advanced mode. Fix Windows so it boots ok. 

Then use Boot-Repair to reinstall grub. It looks like it is having issues reinstalling grub to MBR. You may need to use the advanced mode to run the total reinstall of all of grub. make sure Internet is working as it will download a new copy of grub-pc to install.

If not then ext4 may also need fsck?

---

### Post by gde061-www on 2016-09-16
> **oldfred said:**
> Grub only boots working Windows.

You may need to temporarily reinstall Windows boot loader with your Windows repair flash drive or a Windows type boot loader with Boot-Repair's advanced mode. Fix Windows so it boots ok. 

I got windows up and running ok now. The grub menus for Windows are working fine.  However the ones for ubuntu still crash (see below).

> 
Then use Boot-Repair to reinstall grub. It looks like it is having issues reinstalling grub to MBR. You may need to use the advanced mode to run the total reinstall of all of grub. make sure Internet is working as it will download a new copy of grub-pc to install.

Boot repair still fails.  I have tried with regular repair and advanced mode with the purge grub before reinstall option checked.  The latest boot-repair info log is at [http://paste.ubuntu.com/23188221/](http://paste.ubuntu.com/23188221/)

> 
If not then ext4 may also need fsck?

When the system attempts to load Ubunu, it gets to an Ext4-fs error.  Says something about unable to read itable block.  Then there are a bunch of dump messages with hex codes that are beyond my knowledge.  This happens even if I try starting ubuntu with advanced options, and select "recovery (safe)" mode.  

I went through the terminal in boot-repair environment and ran fsck on dev/sda4.  It found a bunch of issues, and when prompted I chose whatever the default was.  Now the system just crashes with a different error, says something like it can't find /sbin/init or something like that.  

So where that leaves me:  Windows is running fine - which I don't really care about - but there was corruption of the user environment and I had to restore the registry from a backup.  From a USB I can boot into the boot-repair desktop or into gparted.   I can probably pull everything I might care about off off the drive, but I would like to know how to fix this (assuming it's possible) without resorting to rebuilding the OS.  Disturbed that windows repair could frag up a totally separate ext4 partition like this (I had it set up with 4 partitions - boot partition for grub, windows NTFS partition, a Fat32 "bridge" to share data, and an ext4 Ubuntu partition).  

Any advice of other things to try appreciated... Thanks

---

### Post by oldfred on 2016-09-16
Did Windows delete an ext4 partition from the partition table? Windows has done this for years.
 Major Windows updates will  do that. 
Partition is still there and can easily be recovered with testdisk or parted rescue. 

Did you run the full fsck on all ext* partitions?
 #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1 

May be best to see details.
      
 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

