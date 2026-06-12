---
title: "Boot Problems"
date: 2010-03-05
forum: Installation &amp; Upgrades
---

### Post by djailer on 2010-03-05
I originally posted this in hardware - I thought that might have been the problem.  Since then I am wondering if I just don't know what I am doing:rolleyes:

I am waaaay noob so please have patience. Just started on Ubuntu a week ago. I have searched some and cannot find anything on point. I have a W2K Pro SP4 install on the slave D: drive. It is partitioned into to parts. C used to have my primary W2k but I changed out MB and lost it. Both are IDE. Anyway, I got a 320GB SATA HD and stuck it in there. I figured this would be a good place to get my feet wet with Ubuntu. Installed 9.10 easily enough. It did give me some weird memory error over and over - I think it had four sets of 4-5 chars, i.e. 7E777-F8773-FFE45-45343 (not the actual error - just my representation of what I think I remember.) It installed fine and dual boots just great. So...to the point.
Ubuntu can see the C: drive but doesn't see anything on the D: drive.The Palimpsest Disk utility tells me it is 41 GB not recognized - unknown or unused. That is the D drive where the above referenced working and stable W2K is installed. It thinks it is not partitioned and is labeled as /dev/sdc. fdisk -l tells me:

Disk /dev/sdc: 41.2 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7aac7aac

This doesn't look like a partition table
Probably you selected the wrong device.

Device Boot Start End Blocks Id System
/dev/sdc1 1 2502 20097283+ 7 HPFS/NTFS
/dev/sdc2 ? 2503 5005 20105347+ 7 HPFS/NTFS

:popcorn:

Self help update...I don't know if this is good or bad.  Suddenly I can't boot to Ubuntu at all.  Last thing I did was agree to the Auto Updater which installed a bunch of stuff.

I found what purports to be the command line boot process. If I am doing things right I seem to be missing a file....initrd.img. When I look in the initrd file I think there were four files there, but not initrd.img.
I assume I have wubi installed since ls shows one of the drives as LOOP0, which seems unique to the wubi steps. Here is what I followed:
```


ls

```this showed me all the drives it saw. (LOOP0)(hd1)(hd1,1)((hd2)(hd2,1)(fd1) - I think those were it
```


set root=(hdX,Y)

```I tried hd1, hd2,1, hd2,hd2,1,LOOP0 for the drives but got the same result
```


linux /vmlinuz root=/dev/sdxY loop=/ubuntu/disks/root.disk ro

```Again I tried all the combinations for the drive. sr1, sdc1, sda1, sdb1
```

initrd /initrd.img
boot

```This resulted in a lot of lines of code but ended up with a kernel panic message and telling me it couldn't find anything to boot. The drives it saw are listed in the previous code explanation.

Any ideas?

Doug

---

### Post by oldfred on 2010-03-05
A lot of wubi problem solutions are listed here:
Fix for grub2 problem with wubi
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

---

### Post by djailer on 2010-03-05
That was it. Replaced the file and I am back running Ubuntu again. 
Thanks!!!!

Doug

---

