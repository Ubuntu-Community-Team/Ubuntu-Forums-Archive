---
title: "Windows 7 Starter (x86) doesn't boot with dual boot (Ubuntu 14.10)"
date: 2014-12-22
forum: Installation &amp; Upgrades
---

### Post by timbrust3103 on 2014-12-22
Hi there,

sadly my dual boot between *Windows 7 Starter (x86) *and *Ubuntu 14.10 (x86) *is not working anymore.
Whenever I try to boot Windows, it just ends up with a purple screen and nothing else happens (I do not hear the Windows login sound).

I'v read tons of thread and posts/answers, but my problem is still existing. Ubuntu 14.04 didn't worked, too.

Some information about my system (Medion Akoya E1228):
[LIST]
[*]Intel Atom N570 (1.6 GHz)
[*]1GB RAM, vendor not known
[*]Intel GMA 3150
[*]250 GB Hitachi HTS54322
[/LIST]

I've even reinstalled everything.
Just a clean Windows 7 Starter with updates and then the rest of the HDD with Ubuntu, as a dual boot.

Here is my pastebin of boot-repair:
[http://paste.ubuntu.com/9599914/](http://paste.ubuntu.com/9599914/)

Adding *quiet splash *to the GRUB menu didn't help, too.
I'm using *3.16.0-28-generic*, other than that my system is up to date.

However this should be noticed:
Whenever I boot into Windows recovery via an USB stick and repair the MBR to the one Windows ships, Windows is just booting fine ;)

Please let me know if you need more information or more specific one.

Thanks in advance,

Tim

---

### Post by fantab on 2014-12-23
Your bootinfo summary shows a corrupt or an encrypted (or something else that I don't know) swap partitiion:
```
Model: ATA Hitachi HTS54322 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags:

Number  Start   End    Size    Type      File system  Flags
1      1049kB  106MB  105MB   primary   ntfs         boot
2      106MB   189GB  189GB   primary   ntfs
3      189GB   250GB  61.3GB  extended
5      189GB   249GB  60.3GB  logical   ext4
[COLOR=#b22222]6      249GB   250GB  1062MB  logical[/COLOR]
```

```
Failed to mount '/dev/sda6': Das Argument ist ungültig
The device '/dev/sda6' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
mount /dev/sda6 : Error code 12
mount -r /dev/sda6 /mnt/boot-sav/sda6
NTFS signature is missing.
```

I'd suggest you boot from live ubuntu DVD/USB, open Gparted and delete the 6th partition or /dev/sda6. Apply changes.
Create a new partition, type=logical; Use as=linux_SWAP. Apply changes. Quit Gparted.

Open Terminal and run the following:
```
sudo blkid
```

Note down the UUID of the Swap partition or /dev/sda6.

Open Nautilus/Files and open your first, /dev/sda1 installed ubuntu's '/'. Then to /etc/fstab and open it.

Edit /etc/fstab file to replace the UUID of the swap partition, with the one noted from 'blkid' command:

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=35a1107c-b354-4849-96e4-27a8c5ade402 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
[COLOR=#008000]#[/COLOR]**UUID=[COLOR=#b22222]2a916a5d-4779-4b92-b177-dacd50313d53[/COLOR]** none            swap    sw              0       0
[s]/dev/mapper/cryptswap1 none swap sw 0 0[/s]

```

Remove the **[COLOR=#008000]#[/COLOR]** at the beginning of the line. And delete the line which is struck out. Save the file.
Use boot-repair to re-install grub. Reboot and tell us more... don't forget the latest bootinfo summary if the problem persists.

--- With only 1gb of RAM on very basic machine you are better off with lighter *buntu, like Lubuntu or Xubuntu as they require less system resources to work with.

---

### Post by timbrust3103 on 2014-12-23
Still not booting into Windows 7.
My updated paste is here

[http://paste.ubuntu.com/9604738/](http://paste.ubuntu.com/9604738/)

(at least my swap is fixed now)

Thanks in advance again.
Tim

---

### Post by oldfred on 2014-12-23
You cannot install grub to a Windows NTFS partition.

```
 sda2: __________________________________

       File system:       ntfs
    Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v1.99-2.00) is installed in the boot sector of 
                       sda2 and looks at sector 406679632 of the same hard 
                       drive for core.img, but core.img can not be found at 
                       this location. No errors found in the Boot Parameter 
                       Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe


```

Windows has essential boot code of its own in the partition boot sector. It does have a backup, that can be restored if backup is ok.
       Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

    
If you have to totally rebuild the partition boot sector, you need a Windows repair disk and run bootsect.exe.

---

### Post by fantab on 2014-12-23
Did you run the "Recommended Repair", in Boot-repair or did you tweaked around?
Simplest fix would be to re-install Windows (if that is an option) and then use Boot-Repair from Live Ubuntu to re-install Grub.

---

### Post by timbrust3103 on 2014-12-24
> **oldfred said:**
> 
You cannot install grub to a Windows NTFS partition.

...


Why can't I? This setup worked with old ubuntu (like 10.04) versions fine.

> **fantab said:**
> Did you run the "Recommended Repair", in Boot-repair or did you tweaked around?
Simplest fix would be to re-install Windows (if that is an option) and then use Boot-Repair from Live Ubuntu to re-install Grub.

Both, and both had no success.


Any other tips/ideas?
Thanks for reading and have a wonderful Christmas.

Tim

---

### Post by oldfred on 2014-12-24
This is how Windows works, you can just review the photos.
 Pictures here worth 1000+ words - Vista but all Windows with BIOS/MBR
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

But Windows has its own boot code in the partition boot sector. 

While you can install grub legacy to a partition But not NTFS, grub2 should not be installed to a partition. It is forced to convert to blocklists which are hard coded addresses and grub updates or even a fsck may move a file on system and address is wrong. Then you get grub errors and have to reinstall grub.

---

### Post by timbrust3103 on 2015-01-02
Just to notify any future readers:

I solved it by disabling the BIOS *Boot Sector Virus Protection* and everything worked just fine.

Cheers,
Tim

---

