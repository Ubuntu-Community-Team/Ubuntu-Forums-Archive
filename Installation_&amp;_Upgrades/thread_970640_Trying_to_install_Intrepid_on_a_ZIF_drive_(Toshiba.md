---
title: "Trying to install Intrepid on a ZIF drive (Toshiba MK6028GAL)"
date: 2008-11-04
forum: Installation &amp; Upgrades
---

### Post by pirivan on 2008-11-04
Hello,

I have a sample tablet PC loaded with Windows XP on which I want to install Intrepid. I successfully booted Intrepid from a USB stick, resized the NTFS partition to get some space for Intrepid, and proceeded with the installation.

Everything goes well, there are no reported installation errors. I then reboot the tablet and successfully get into the Grub menu. From there I can boot XP with no problems, but when I select the Linux kernel the screen goes blank right away, and I mean it, right away. I don't believe the Linux kernel gets to be loaded at all; the tablet doesn't respond to any key.

If I boot from the USB stick again, I can see the new partitions allocated to Intrepid (one swap and one for /). The root file system is there, fully populated, and I can even chroot into it without problems. I checked the uuid values for the partition and they seem OK, I mean, the uuid of the partitions in grub's menu.list file match the output of the vol_id command when using the live system.

The tablet has this [Toshiba ZIF drive]("http://www.toshibastorage.com/main.aspx?Path=StorageSolutions/1.8-inchHardDiskDrives/MK6028GAL/MK6028GALSpecifications") and I wonder if there is something specific that has to be done with it. I haven't fully reformatted the entire drive because I need to keep the XP partition.

Attached you will find some system info taken while running the live system. I'd appreciate any suggestions on what to do next.

Thanks you,

-- 
Pedro

```
ubuntu@ubuntu:~$ sudo fdisk -l /dev/sda

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc40ac40a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825        4079     2048287+  82  Linux swap / Solaris
/dev/sda3   *        4080        7296    25840552+  83  Linux

ubuntu@ubuntu:~$ dmesg|grep sda
[    9.113860] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors (60012 MB)
[    9.113940] sd 0:0:0:0: [sda] Write Protect is off
[    9.113950] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    9.114085] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    9.114329] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors (60012 MB)
[    9
.114403] sd 0:0:0:0: [sda] Write Protect is off
[    9.114412] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    9.114546] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    9.114562]  sda:<6>usb 1-8: configuration #1 chosen from 1 choice
[    9.409018]  sda1 sda2 sda3
[    9.434219] sd 0:0:0:0: [sda] Attached SCSI disk
[   99.817898] Adding 2048276k swap on /dev/sda2.  Priority:-1 extents:1 across:2048276k
[  724.461889] EXT3 FS on sda3, internal journal

ubuntu@ubuntu:~$ sudo mount /dev/sda3 /mnt

ubuntu@ubuntu:~$ cat /mnt/boot/grub/menu.lst (abridged)
title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		a491c8f3-a51f-40a4-abca-c88864b6c56d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=a491c8f3-a51f-40a4-abca-c88864b6c56d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		a491c8f3-a51f-40a4-abca-c88864b6c56d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=a491c8f3-a51f-40a4-abca-c88864b6c56d ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		a491c8f3-a51f-40a4-abca-c88864b6c56d
kernel		/boot/memtest86+.bin
quiet

title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
chainloader	+1

```

---

