---
title: "Installing GRUB onto a RAID 5"
date: 2010-08-23
forum: Installation &amp; Upgrades
---

### Post by Gralamin on 2010-08-23
So, I [recently]("http://ubuntuforums.org/showthread.php?t=1558762") installed Ubuntu on a (now) Triplebooting RAID 5 system. However, the setup was not able to install GRUB. This means I cannot boot into Ubuntu currently.

The following are acceptable outcomes for me:
1) Installing GRUB as the primary bootloader, allowing me to boot into Linux, Windows 7, or Windows XP.
2) Installing GRUB as the primary bootloader, but allowing me to boot into the Windows 7 Bootloader as well as Ubuntu.
3) Installing GRUB as a secondary bootloader that can be accessed through the Windows 7 Bootloader.

My current config, according to gparted with kpartx installed is:
```

Partition                               File system   Label        Flags
/dev/mapper/isw_cecafgaibc_Volume01     ntfs          Windows XP  boot
unallocated                             unallocated   -            -
/dev/mapper/isw_cecafgaibc_Volume02     extended      -            lba
  /dev/mapper/isw_cecafgaibc_Volume07   ext4          Ubuntu        -
  /dev/mapper/isw_cecafgaibc_Volume08   linux-swap    linswap        -
  /dev/mapper/isw_cecafgaibc_Volume05   ntfs          Windows 7        -
  /dev/mapper/isw_cecafgaibc_Volume06   ntfs          winswap        -
unallocated                             unallocated   -           -

```

So how do I go about installing GRUB so that this will work?

---

### Post by ronparent on 2010-08-23
As you have found, there are glitches installing grub 2 with a raid. Check out the section titled 'Reinstalling GRUB 2' in this reference:

[https://help.ubuntu.com/community/Grub2#Post-Restoration%20Commands](https://help.ubuntu.com/community/Grub2#Post-Restoration%20Commands)

Just be sure to use the root location /dev/mapper/isw_cecafgaibc_Volume07 and the entire array, /dev/mapper/isw_cecafgaibc_Volume0 (or whatever tag designates the entire array in /dev/mapper/) as the target for the grub MBR on the raid.

---

### Post by Gralamin on 2010-08-24
Following that guide has left me with grub command line, and no list (I tried mounting and chroot to update grub through the live cd). I'm guessing another driver or something is required. The generated menu file is not being read, and if I look at it, does not include other operating systems.

I've tried method 1 and 2, now trying method 3

Edit: Still not working. If I use the grub command line though, I can see that it can detect all of the partitions - though it thinks the ubuntu one is ext2 instead of 4.

Edit2: And if I type
```
grub> configfile (hd0,7)/boot/menu.list
```
I receive:
```
error: unknown command 'default'.
error: unknown command 'timeout'.
error: unknown command 'hiddenmenu'.
error: unknown command 'title'.
error: no such partition.
error: unknown command 'kernel'.
error: you need to load the kernel first.
error: unknown command 'title'.
error: no such partition.
error: unknown command 'kernel'.
error: you need to load the kernel first.
error: unknown command 'title'.
error: no such partition.
error: unknown command 'kernel'.
error: unknown command 'title'.
error: no such partition.
error: unknown command 'kernel'.
```

---

### Post by Gralamin on 2010-08-24
Fixed it, although it might be the wrong version.

Steps:
1) Setup for chroot as in step 3 of the above linked guide
2) make sure kpartx is installed
3) chroot in
4) purge grub2 (See the documentation)
5) Install grub-pc through sudo apt-get, selecting the raid partition as the volume to use.
6) restart!

---

### Post by ronparent on 2010-08-24
Interesting. Kpartx should have no play with grub. Grub as distributed with 10.04 must have some bug (that would explain some of the glitchiness). It took me three days to fix grub to allow me to boot my computer after a Maverick install. Grub had written boot loaders to everywhere possible unintended which pointed nowhere even overwriting the win 7 boot loader on my ssd (which should have been left untouched)

Great to see you have things working. It's been a struggle but I think you will find Lucid worth it.

---

