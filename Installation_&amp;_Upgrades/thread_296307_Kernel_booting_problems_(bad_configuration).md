---
title: "Kernel booting problems (bad configuration?)"
date: 2006-11-09
forum: Installation &amp; Upgrades
---

### Post by xfreeman86 on 2006-11-09
Howdy all,

I posted this thread originally in the Mailing List group, but to no avail (maybe that forum is just for topics currently being discussed on the mailing list?). So I am bringing it here, but with fair warning: this does not have anything to do directly with Ubuntu. I've been getting help from others' topics on the Ubuntu Forums for awhile now, so this is the first place I wanted to go for my own problem.

I have been trying these past few days to compile the latest snapshot of the kernel (2.6.19-rc4) from kernel.org with support for the Devicescape wireless stack more or less following these instructions:

for download and some configuration: [http://www.linuxquestions.org/questions/showthread.php?t=444476](http://www.linuxquestions.org/questions/showthread.php?t=444476)

for more configuration and compilation: [http://ubuntuforums.org/showthread.php?t=217657&highlight=compile+kernel](http://ubuntuforums.org/showthread.php?t=217657&highlight=compile+kernel)

I am running Kubuntu Edgy on a Dell Inspiron E1505/6400 which has a built-in Broadcom 4311 chipset wireless card. The driver module bcm43xx, after installing proper firmware using bcm43xx-fwcutter, allows me to scan, set essid, and enter monitor mode, but not connect or set rate, thus I'm looking to upgrade.

I used to get this error:
```
Kernel panic: VFS: Unable to mount root fs on unknown-block(0,0)
```
as well as this:
```
FATAL: Could not load /lib/modules/.../modules.dep
```
but fixed it by adding ext3 filesystem (by module) and initrd support to the kernel configuration:

File systems -> Ext3 journalling file system support (EXT3_FS)
Device Drivers -> Block devices -> Initial RAM filesystem and RAM disk (initramfs/initrd) support (BLK_DEV_INITRD)

Now I have a new problem. During bootup, it hangs with this last message:
```
Begin: Waiting for root file system... ...
```
I found a very similar situation to my own at [https://launchpad.net/distros/ubuntu/+source/initramfs-tools/+bug/67256](https://launchpad.net/distros/ubuntu/+source/initramfs-tools/+bug/67256)
I tried the solution posted there:
```
sudo update-initramfs -u -k 2.6.19-rc4
```
but it did not work.

I know I read some stuff during all these problems about compiling support for my SATA hard disk, but cannot recall exactly where, what it meant, or if it pertains to this. I've done a lot of searching on my own, but seem to have hit a wall. I'm lost right now and looking for help. Thanks in advance!

---

### Post by raingrove on 2006-12-01
I am having the same problem now. Have you managed to fix it?

---

### Post by xfreeman86 on 2006-12-17
No, I haven't been able to find any help since I posted this.

---

