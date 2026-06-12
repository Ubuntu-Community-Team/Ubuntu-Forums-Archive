---
title: "Ubuntu is installed, but no way to get to it"
date: 2008-03-01
forum: Installation &amp; Upgrades
---

### Post by rsp385 on 2008-03-01
So here's my situation...

I recently got a new computer that came pre-loaded with Windows XP.  The machine has 4 disks, with the first two in a RAID 0 array and the other two not configured for RAID.

I attempted to install Ubuntu 7.10 on the third disk, which seemed like an ideal place because it contained no data and I could partition it easily.  The installation proceeded without issue until it came time to reboot.  Yikes -- a grub error! (Can't recall the exact error code, but it was in stage 1.5).  It seems that my MBR had become corrupted (possibly due to the RAID setup?) and I ultimately had to reformat everything and reinstall Windows on the RAID disks.

Now I'm back more or less to where I started, with Windows XP working fine again.  While the Ubuntu partition is still there on the third disk, I have no way of booting into it, because the MBR only knows about Windows!

What's the best way to dual-boot my existing Windows XP and Ubuntu installations now?  In other words, how can I set up a boot menu that will let me boot into the Ubuntu partition I already have, without going through the whole installation process again?  Can I do this without buying an expensive tool like PartitionMagic (which apparently doesn't support large disks anyway)?

Thanks...

---

### Post by scragar on 2008-03-01
grub can reinstall itself if you have a live CD.

[http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)

---

### Post by rsp385 on 2008-03-01
OK, but why would grub work this time if it didn't work when I first tried to install it?  It seems like it choked on the fact that the Windows XP installation was on RAID disks...at least that's my guess.

---

### Post by scragar on 2008-03-01
just give it a try and see if it works, worst that can happen(use the second posters steps if you can, they are less prone to errors and such) is that grub still doesn't work and it gives you an error message when reinstalling it that can further help isolate the problem.

---

### Post by Victormd on 2008-03-01
When you're installing the OS's on different physical drives, GRUB sometimes has a hard time figuring out where to copy certain files (and where to look for them during boot). Probably, what happened was that GRUB copied the necessary files to boot on to the drive where Ubuntu was installed while the boot order (in BIOS) is set to look first on the HD where windows is installed (just a thought). I usually partition my primary HD to install my OS's and that's always worked for me.

---

### Post by dstew on 2008-03-01
> Can't recall the exact error code, but it was in stage 1.5Probably grub was installed without the realization that your RAID was there, so it was looking for its menu in the wrong partition. You probably did not have to reinstall Windows, only do fixmbr from the Recovery Console. But anyway, to get grub to install correctly you might have to install grub manually so that it is set up right.

At present, Ubuntu is probably there on your third hard drive, correct? To make sure, you can boot a Live CD and post the output of sudo fdisk -l entered on the Terminal command line.

---

### Post by rsp385 on 2008-03-02
> **dstew said:**
> At present, Ubuntu is probably there on your third hard drive, correct? To make sure, you can boot a Live CD and post the output of sudo fdisk -l entered on the Terminal command line.

Right, here's what fdisk -l shows:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x06850685

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      243201  1953512001    7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000101

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2b182b17

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       10942    87891583+  83  Linux
/dev/sdc2           10943       12158     9767520   82  Linux swap / Solaris
/dev/sdc3           12159      121601   879100897+   7  HPFS/NTFS

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
16 heads, 63 sectors/track, 1938021 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x47e53ee9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1     1938018   976761040+   7  HPFS/NTFS
```


So if I did decide to reinstall grub from the live CD, what grub commands would I use to make both /dev/sda1 and /dev/sdc1 bootable?  And again, why should I expect that this grub installation would be any more successful than when it failed the first time?

I wonder if making the first two disks non-RAID would help things.  The Ubuntu Live CD has no problem reading from the NTFS partition on my fourth disk, but not the RAID disks ("Invalid MFT error" followed by some gibberish about FakeRAID/SoftRAID)

---

### Post by dstew on 2008-03-02
Yes, grub cannot detect your RAID properly because it doesn't have the software to do that, only an operating system can. Usually, to dual-boot a RAID, you need to have at least a /boot partition that is not part of the RAID that grub can use to get the system booted. You can install grub so that it gets its stage2 from the un-RAIDed /dev/sdc1 partition. The issue is where to install stage1 and stage1.5, which makes up the initial boot loader.

Usually, grub stage1 is installed into the MBR of the boot disk, and stage1.5 onto track0 of the same disk. The problem is, that some logical volume management setups use track0 for its own purpose. That is, there may not be a regular MBR/track0 available on your /dev/sda disk to put grub stage1 and stage1.5. Only you would know if you have your disk set up this way.

The safest thing to do is try to install grub stage1 and stage1.5 onto an unRAIDed disk. Then, you could set up the menu.lst file to get everything working (maybe--see below). The problem with that is, of course, your BIOS would have to be able to boot /dev/sdc.

What you need to know, is exactly how your BIOS boots your RAID. Does it use the track0 and MBR to get Windows to start the RAID, or does it have a special ability to boot a RAID directly? If it is the second, it might not be possible to get grub to boot the RAIDed Windows install. Grub boots Windows by chainloading, which depends on a track0 bootloader I think. So, my best guess is to install grub onto the MBR of /dev/sdc like this:```
root (hd2,0)
setup (hd2)
quit
```These commands are entered from a Live CD boot, grub command line.

---

