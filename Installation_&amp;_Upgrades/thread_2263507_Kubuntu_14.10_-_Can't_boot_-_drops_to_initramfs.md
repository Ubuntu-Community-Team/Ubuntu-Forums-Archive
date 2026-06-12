---
title: "Kubuntu 14.10 - Can't boot - drops to initramfs"
date: 2015-02-01
forum: Installation &amp; Upgrades
---

### Post by pnips on 2015-02-01
Hello. I recently purchased a 2015 Dell XPS 13. I wiped windows and installed Kubuntu. It won't boot, and drops me to the following screen:

-------------------------------------------------------------------------------------------------
Gave up waiting for root device. Common problems:
 - Boot args (cat /proc/cmdline)
   - Check rootdelay= (did the system wait long enough?)
   - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/96894e84-4cdd-46b2-ad9b-9f50088d04e0 does not exist. Dropping to a shell!


BusyBox v1.22.1 (Ubuntu 1:1.22.0-8ubuntu1) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initiramfs) _
---------------------------------------------------------------------------------------------------

It does not appear to be a rootdelay issue. I have tried waiting a few minutes and entering exit: it just drops back to the same prompt.

The UUID listed also appears to be correct; see below. I also tried changing the UUID in /etc/fstab to "/dev/sda1": no change. It still dropped to initramfs and complained about not finding the UUID.

I can use a liveUSB to boot, and when I do the drive shows up and appears to be fine. I ran e2fsck on each partition and it showed no errors.

Below are a few pieces of relevant info:

----------------------------------------------------------------------------------------------------------------------------
sudo blkid

/dev/sda1: UUID="96894e84-4cdd-46b2-ad9b-9f50088d04e0" TYPE="ext4" PARTUUID="4b5e7a41-01"
/dev/sdb1: UUID="b953e126-868b-48b8-a70f-43e448d5183c" TYPE="ext4" PARTUUID="07fd663e-01"
/dev/loop0: TYPE=""squashfs"
/dev/sda5: UUID="172779ec-4749-4559-8cf2-00b6926f7c52" TYPE="swap" PARTUUID="4b5e7a41-05"
----------------------------------------------------------------------------------------------------------------------------

sudo fdisk -l

Disk /dev/loop0: 1021.3 MiB, 1070915584 bytes, 2091632 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk /dev/sda: 119.2 GiB, 128035676160 bytes, 250069680 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x4b5e7a41

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1  *         2048 242450431 242448384 115.6G 83 Linux
/dev/sda2       242452478 250068991   7616514   3.6G  5 Extended
/dev/sda5       242452480 250068991   7616512   3.6G 82 Linux swap / Solaris

Disk /dev/sdb: 15.1 GiB, 16231956480 bytes, 31703040 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x07fd663e

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdb1  *       32 31703039 31703008 15.1G 83 Linux
----------------------------------------------------------------------------------------------------------------------------
And here is a copy of /etc/fstab

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=96894e84-4cdd-46b2-ad9b-9f50088d04e0 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=172779ec-4749-4559-8cf2-00b6926f7c52 none            swap    sw              0       0
----------------------------------------------------------------------------------------------------------------------------

Any help is appreciated. Thanks!


Update 1:
I also tried running boot-repair. It said it was successful, but I still have the same problem. Boot-repair listed the following URL:
[http://paste.ubuntu.com/10000226/](http://paste.ubuntu.com/10000226/)

---

