---
title: "dualboot: winXP won't boot after removing old kernel"
date: 2010-06-17
forum: Installation &amp; Upgrades
---

### Post by vangop on 2010-06-17
Hi guys,
I have winxp and ubuntu 10.04 dualboot.
They were working ok. 
Today I removed old *21 kernel image and headers so grub updated the confs. That's all I did that could cause the win no longer boot.
It starts booting, the screen goes black and the PC reboots. I tried safe mode, it started to load some dlls as it usually shows in safe mode but then still reboot.
Any idea?
```
$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe941e941

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5221    41937651    7  HPFS/NTFS
/dev/sda2            5222       18242   104584961    7  HPFS/NTFS
/dev/sda3           18242       19093     6837248   83  Linux
/dev/sda4           19093       19458     2928641    5  Extended
/dev/sda5           19093       19458     2928640   82  Linux swap / Solaris

```

Part of the grub.cfg with win seem to be ok:
```
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
        insmod ntfs
        set root='(hd0,1)'
        search --no-floppy --fs-uuid --set f0d8d10bd8d0d148
        drivemap -s (hd0) ${root}
        chainloader +1
}
### END /etc/grub.d/30_os-prober ###

```

```
$ ll /etc/grub.d/
total 56
drwxr-xr-x   2 root root  4096 2010-05-31 09:52 ./
drwxr-xr-x 139 root root 12288 2010-06-17 17:27 ../
-rwxr-xr-x   1 root root  4444 2010-04-13 16:59 00_header*
-rwxr-xr-x   1 root root  1416 2010-04-13 16:40 05_debian_theme*
-rwxr-xr-x   1 root root  4594 2010-04-13 16:59 10_linux*
-rwxr-xr-x   1 root root   918 2010-03-23 11:37 20_memtest86+*
-rwxr-xr-x   1 root root  6605 2010-04-13 16:59 30_os-prober*
-rwxr-xr-x   1 root root   214 2010-04-13 16:59 40_custom*
-rw-r--r--   1 root root   483 2010-04-13 16:59 README

```

---

### Post by darkod on 2010-06-17
I can't really see how removing a kernel would influence booting XP.

No ideas from me. :(

PS. You can try the boot info script, maybe it will show something. Instructions here:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

---

### Post by leorolla on 2010-06-17
It was probably not the removal of the old kernel but may be the grub-update that is triggered when the kernel is removed.

Did you try SuperGrubDisk?

If you can boot from USB, something you can try is to backup the MBR contents and replace it by a Windows-like MBR, which will just chainload the first partition (where I guess your Windows is located). If that doesn't work then I will guess the problem is with your Windows install and the removing kernel thing was just a coincidence.

---

### Post by vangop on 2010-06-18
Guess I figured. It does have nothing to do with the old kernel removal. I messed up the win by linking it as wine c: drive and running some apps. So some libs must have been corrupted.
Thanks for your input!

---

