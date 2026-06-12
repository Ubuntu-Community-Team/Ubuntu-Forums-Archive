---
title: "Ubuntu server 14.04 LVM install via usb - only boots with usb stick in"
date: 2014-07-14
forum: Installation &amp; Upgrades
---

### Post by sjhupp on 2014-07-14
I assume this is a grub and/or LVM issue, but I can't seem to fix it, so asking for help.
I installed 14.04 server off a usb stick, and used a guided LVM install *80GB of a 160GB disk), and I made sure to say no to default install and put grub on sdb, which is my 160GB drive (8GB flash is sda).
But I cannot boot from the hdd without the usb stick in the PC, so clearly I did something wrong :mad:
So I left the usb stick it in and tried to reinstall grub (ie [http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd](http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd)) to sdb but made no difference.
So here's where I'm at now:

```
[I]simon@cavetroll:~$ sudo fdisk -l

Disk /dev/sda: 8004 MB, 8004304896 bytes
241 heads, 36 sectors/track, 1801 cylinders, total 15633408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x90909090

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    15630335     7814144    c  W95 FAT32 (LBA)

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004e4d6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048      499711      248832   83  Linux
/dev/sdb2          501758   312580095   156039169    5  Extended
/dev/sdb5          501760   312580095   156039168   8e  Linux LVM

Disk /dev/mapper/cavetroll--vg-root: 71.4 GB, 71412219904 bytes
255 heads, 63 sectors/track, 8682 cylinders, total 139476992 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/cavetroll--vg-root doesn't contain a valid partition table

Disk /dev/mapper/cavetroll--vg-swap_1: 8585 MB, 8585740288 bytes
255 heads, 63 sectors/track, 1043 cylinders, total 16769024 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/cavetroll--vg-swap_1 doesn't contain a valid partition table[/I]

Some mention of not a valid partition table above indicate a problem I assume?
And looking at more details:

[I]simon@cavetroll:~$ sudo parted -l
Model: SanDisk Cruzer Switch (scsi)
Disk /dev/sda: 8004MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  8003MB  8002MB  primary  fat32        boot, lba


Model: ATA ST9160821AS (scsi)
Disk /dev/sdb: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type      File system  Flags
 1      1049kB  256MB  255MB  primary   ext2         boot
 2      257MB   160GB  160GB  extended
 5      257MB   160GB  160GB  logical                lvm


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/cavetroll--vg-swap_1: 8586MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system     Flags
 1      0.00B  8586MB  8586MB  linux-swap(v1)


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/cavetroll--vg-root: 71.4GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  71.4GB  71.4GB  ext4[/I]

And if of any use:

[I]simon@cavetroll:~$ sudo swapon -s
Filename                                Type            Size    Used    Priority
/dev/mapper/cavetroll--vg-swap_1        partition       8384508 0       -1[/I]

[I]simon@cavetroll:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/cavetroll--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sdb1 during installation
UUID=266a6ca5-1010-4f6c-ac5e-d3d9107e710f /boot           ext2    defaults        0       2
/dev/mapper/cavetroll--vg-swap_1 none            swap    sw              0       0[/I]
```

I never had these problems with 12.04... but didn't use LVM.
So could anyone help please?
Thanks.

---

### Post by sudodus on 2014-07-14
I think you installed the bootloader into the USB drive instead of into the target drive. Try to repair the system according to this link

[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

If still no go, and the system is new, maybe it is easiest to reinstall it and get the bootloader to the right place at once. I don't know LVM well, and can't help much with details, so let us hope someone who knows will chip in and help you, if this turns out to be more complicated.

---

### Post by sjhupp on 2014-07-14
Yep, did reinstall grub from the link I posted up top (seems the same). Installed to sdb, which is the 160GB drive. But I assume LVM makes a difference, as it is complaining about partition table.
If I try to boot from the hdd, it just reboots (and repeats cycle). If I boot from the usb (YUMI with 14.04 server) I can select boot from first hdd and it boots up.
Any BIOS settings worth looking at?
I did have AHCI set for this install - bad idea?
I actually did a clean install before this, but did the default grub install, which seemed to put it on the usb drive, so this time I made sure to put on sdb.
Then reinstalled, check installed and updated grub.
Don't get a grub menu either.
No idea...

---

### Post by sudodus on 2014-07-15
> **sjhupp said:**
> Yep, did reinstall grub from the link I posted up top (seems the same). Installed to sdb, which is the 160GB drive. But I assume LVM makes a difference, as it is complaining about partition table.
If I try to boot from the hdd, it just reboots (and repeats cycle). If I boot from the usb (YUMI with 14.04 server) I can select boot from first hdd and it boots up.
Any BIOS settings worth looking at?
I did have AHCI set for this install - bad idea?

If it can boot via the USB drive I think the BIOS settings are OK. It should work with AHCI, but you can try to change that setting and see what happens. Are you sure, that the BIOS is set to boot from the 160GB drive, when it fails. Maybe it tries to boot from some other drive.
> 
I actually did a clean install before this, but did the default grub install, which seemed to put it on the usb drive, so this time I made sure to put on sdb.
Then reinstalled, check installed and updated grub.
Don't get a grub menu either.
No idea...

If there was only one system (Ubuntu Server) when you installed, the grub menu will not be displayed by default. But you should be able to get it by pressing the left shift key ('shift to upper case', not 'caps locked'). But I don't think we are getting closer ...

I think we need help from someone who knows about LVM.

---

### Post by sjhupp on 2014-07-15
Ok, made some progress.
Did change to the first sata port and did yet another LVM install, and as it was sda let grub go in auto.
Tried to reboot and again gets in reboot cycle.
But selecting the boot options, then choosing the drive (it's the only one in the pc mind you) it did boot.
I then grabbed another drive and replaced it, and tried another install with AHCI setting sin BIOS, but installed failed/hung. So I reset BIOS settings, and put back in the previos drive, and with legacy/ID settings in BIOS it's now booted up a few times.
Must be something in there that it doesn't like.
Anyway, time to config the server (finally!)...
Thanks for the suggestions.

---

### Post by sudodus on 2014-07-16
You are welcome :-)

I'm glad you managed to get your system working. If this booting issue is solved, please click on Thread Tools at the top of the page and mark this thread as SOLVED.

If you have other problems, please make a new thread with a good descriptive title and in the best forum, for example for server issues

[URL="http://ubuntuforums.org/forumdisplay.php?f=339"]Server Platforms
[/URL]

---

