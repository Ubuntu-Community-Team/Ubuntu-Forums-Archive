---
title: "Trying to setup 3TB ext. USB drive as bootable with GPT"
date: 2011-09-13
forum: Installation &amp; Upgrades
---

### Post by brc816 on 2011-09-13
I've been trying to study various other threads, such as
[URL="http://ubuntuforums.org/showthread.php?t=1843547"]
[/URL] and [http://ubuntuforums.org/showthread.php?t=1838078]("http://ubuntuforums.org/showthread.php?t=1838078") in an attempt to set up a newly-purchased Seagate 3TB external USB drive with GPT partitioning and use it to boot Ubuntu Oneiric and, in the future, additional Linux distributions, without perturbing my day-to-day laptop configuration.

My laptop is a 3.5 year old HP dv9000z with 4GB of memory, AMD Turion64 dual core CPU, NVIDIA GeForce 6150 graphics and a relatively vanilla Phoenix BIOS with, apparently, no (U)EFI capabilities. There are TWO 80GB SATA disk drives installed, the primary has Windows XP Media Edition (and its maintenance/re-installation partition), and the other drive has openSUSE 11.4.
GRUB 0.97 was installed by openSUSE, and I can either let it
boot openSUSE 11.4 automatically, or select Windows XP if I
really want to boot that. I have a Western Digital 250GB external
USB drive with standard old-fashioned MBR partitions and GRUB 0.97 (+/-, i.e. NOT GRUB2), and when it's plugged in prior to power-up, I can then boot various other distributions (Fedora, Natty, Mageia, ...) as desired. Yes, the BIOS boot device ordering is set correctly: DVD/CD, USB disk, internal hard disk, USB Floppy, ...

I'm trying to do something like that with the new 3TB. After
some fits and starts, I installed 'gdisk' on my openSUSE 11.4
system and used it to repartition using GPT. This drive has
4096 byte sectors. I've even been able to install Oneiric into a partition, and Fedora 16 to two others (/, /boot) as the latter is rumored to finally being able to cope with GPT and GRUB2.

However, I've not been able to boot either system and, in fact, can't even get a "GRUB>" prompt - the BIOS acts like the drive isn't there and starts the GRUB 0.97 on the first hard drive.
(As an aside, I have an Acer Aspire netbook with an Insyde H2O
EFI BIOS that boots an external 1TB with GPT and Ubuntu/Natty's
GRUB2 beautifully). openSUSE 11.4 comes up smiling, although the drive ordering is different (the 3TB shows up as /dev/sdb, the
Windows disk is /dev/sda, the openSUSE 11.4 disk is /dev/sdc).

My suspicion is that I've messed up the (boot block) and/or other
important partition tables by using gparted, fdisk, and other tools (even if just to look at something). I'm prepared to wipe the drive (dd if=/dev/zero... comes to mind!) as necessary.

Output from gdisk on openSUSE 11.4 as invoked as root, having plugged the 3TB drive in long after booting the system:

```
linux-9mjd:/home/obfuscated # gdisk /dev/sdc
GPT fdisk (gdisk) version 0.7.2

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.

Command (? for help): print
Disk /dev/sdc: 732566645 sectors, 2.7 TiB
Logical sector size: 4096 bytes
Disk identifier (GUID): D8FDAD5C-8335-46A3-BA1C-D44CF7D2C31E
Partition table holds up to 128 entries
First usable sector is 6, last usable sector is 732566639
Partitions will be aligned on 256-sector boundaries
Total free space is 626529130 sectors (2.3 TiB)
                                                                                                                
Number  Start (sector)    End (sector)  Size       Code  Name                                                   
   1             256             511   1024.0 KiB  EF02  BIOS boot partition                                    
   2             512          131583   512.0 MiB   EF00  ext4                                                   
   3          131584         1180159   4.0 GiB     8200  Linux swap                                             
   4         1180160        27394559   100.0 GiB   0700  Linux filesystem
   5        27394560        53608959   100.0 GiB   8300  Linux filesystem
   6        53608960        79823359   100.0 GiB   8300  Linux filesystem
   7        79823360       106037759   100.0 GiB   EF00  Ubuntu
```

I tried to create 1MiB BIOS boot partition (worked nicely on my netbook's 1TB), a 512MB /boot partition for F16 on the second partition, a 4GB swap partition, and then four 100GB partitions, one for each distro of interest. Oneiric is installed on partition 7, Fedora 16 root is on partition 4.

I've tried reinstalling ("grub-install") GRUB2 several times, even after booting the Oneiric Live CD and chrooting to the on-disk installation and using apt-get to update it to ensure that I had the latest-n-greatest bits. I'm assuming that I either don't understand GPT and GRUB2 well enough, or I've made a rash assumption about what can be legally/safely done. Any help would, of course, be greatly appreciated!

Thanks in Advance!

---

### Post by srs5694 on 2011-09-13
> **brc816 said:**
> My laptop is a 3.5 year old HP dv9000z with 4GB of memory, AMD Turion64 dual core CPU, NVIDIA GeForce 6150 graphics and a relatively vanilla Phoenix BIOS with, apparently, no (U)EFI capabilities.
...
After some fits and starts, I installed 'gdisk' on my openSUSE 11.4
system and used it to repartition using GPT. This drive has
4096 byte sectors.

A disk with 4096-byte sectors has an MBR size limit of 2^32 * 4096 bytes, or 16 TiB. Thus, you can safely use MBR on this disk, at least from a disk and partition size perspective. That said, I personally prefer and recommend GPT for Linux-only installations even when it's not required from a size perspective. Also, the fact that you've already done several installations may make it easier to proceed by using what you've got than by repartitioning.

> However, I've not been able to boot either system and, in fact, can't even get a "GRUB>" prompt - the BIOS acts like the drive isn't there and starts the GRUB 0.97 on the first hard drive.

Two possible causes occur to me:


[list]
[*]Your BIOS may have a bug that's preventing it from booting from a GPT disk. I describe some such problems [here.](http://www.rodsbooks.com/gdisk/bios.html) The most common cause of this problem is a bug that's most common on Intel-branded motherboards, although I've heard of cases of it on others, that prevents the board from booting if the MBR doesn't have any partition that's marked with a "boot" (aka "active") flag. The solution is to use Linux's fdisk (*not* parted or any other libparted-based tool!) to set the "boot" flag on the single 0xEE protective partition on the disk. You do this with the "a" option in fdisk, followed by "w" to save your changes.
[*]Your BIOS may have limitations that prevent it from booting from a disk with 4096-byte sectors. If this is the case, the only solution I can think of is to place your Linux boot loader on one of your internal disks and use that to control the boot process, possibly even including loading the Linux kernel and initial RAM disk from the internal disk. Since you've got OpenSUSE on the second internal disk, you might be able to piggyback your other OSes' boot processes off of it by writing appropriate boot loader rules in OpenSUSE. Post back with your current OpenSUSE /boot/grub/menu.lst or /boot/grub/grub.conf file and information on where your Ubuntu and Fedora kernels and initial RAM disks are if you need help making these changes.
[/list]


It's possible that neither of these is the true cause of the problem, though; I could be missing something or be ignorant of some important fact. Nonetheless, both possibilities are worth investigating. If I had to place a bet, I'd say the 4096-byte issue is the more probable cause; however, setting the boot flag on the protective 0xEE partition is the easier cure, so it's probably best to start by doing that. (If it doesn't help, you can always undo the change.)

> My suspicion is that I've messed up the (boot block) and/or other
important partition tables by using gparted, fdisk, and other tools (even if just to look at something). I'm prepared to wipe the drive (dd if=/dev/zero... comes to mind!) as necessary.

I doubt if you've done any damage that necessitates such radical action. At worst, you could wipe the partition table by using parted or GParted to create a fresh partition table (MBR or GPT) or by using the 'z' option on gdisk's experts' menu. Either option will be much quicker than wiping the whole disk!

Below are comments that aren't related to your main problem....

> Output from gdisk on openSUSE 11.4 as invoked as root, having plugged the 3TB drive in long after booting the system:

```
linux-9mjd:/home/obfuscated # gdisk /dev/sdc
GPT fdisk (gdisk) version 0.7.2

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.

Command (? for help): print
Disk /dev/sdc: 732566645 sectors, 2.7 TiB
Logical sector size: 4096 bytes
Disk identifier (GUID): D8FDAD5C-8335-46A3-BA1C-D44CF7D2C31E
Partition table holds up to 128 entries
First usable sector is 6, last usable sector is 732566639
Partitions will be aligned on 256-sector boundaries
Total free space is 626529130 sectors (2.3 TiB)
                                                                                                                
Number  Start (sector)    End (sector)  Size       Code  Name                                                   
   1             256             511   1024.0 KiB  EF02  BIOS boot partition                                    
   2             512          131583   512.0 MiB   EF00  ext4                                                   
   3          131584         1180159   4.0 GiB     8200  Linux swap                                             
   4         1180160        27394559   100.0 GiB   0700  Linux filesystem
   5        27394560        53608959   100.0 GiB   8300  Linux filesystem
   6        53608960        79823359   100.0 GiB   8300  Linux filesystem
   7        79823360       106037759   100.0 GiB   EF00  Ubuntu
```

Assuming those partition names are accurate, the /dev/sda2 and /dev/sda7 partitions both have improper type codes -- EF00 is gdisk's code for an [EFI System Partition (ESP),](http://en.wikipedia.org/wiki/EFI_System_partition) which is almost certainly useless on your computer, and which should normally have a FAT filesystem. The ESP holds EFI boot loaders and other files that are used by the firmware. Unfortunately, libparted identifies these partitions by giving them a "boot flag" -- a flag of the same name that's used to identify bootable partitions under MBR. This causes confusion at best. You should probably set these two have type codes of 0700 or 8300. An improper type code is unlikely to be causing your boot problems, but it could cause confusion down the line. In a worst-case scenario, some utility could get confused and try creating a fresh FAT filesystem on one or both of these partitions. That's unlikely, but changing the type code is easy protection.

The 0700 type code (used on your /dev/sda4) is the type code for Microsoft filesystems. Linux has generally used the same type code itself, so you'll often see it on Linux filesystems. Recently, the libparted developers and I (I'm the author of gdisk) agreed on a new type code for Linux filesystems, which gdisk reports as 8300. The main advantage of using 8300 rather than 0700 is that 8300 partitions won't show up under Windows Vista/7 as "unformatted;" Windows will ignore them. Since you've only got Windows XP on this computer, and XP doesn't understand GPT disks, there's little to recommend one over the other, unless you think you might want to upgrade Windows or move the disk to another computer in the future, in which case 8300 makes more sense.

For the most part, Linux ignores partition type codes, so these issues (including the improper ESP type codes on two partitions) are mostly of concern for non-Linux OSes. Setting them appropriately can minimize the risk of future confusion, though.

---

### Post by brc816 on 2011-09-15
srs5694 and I have been exchanging some private e-mails on this issue. I have a number of ways I can attempt to solve this issue, which I'm still mulling over.

First, I might be successful if I re-partition the disk using MBR and a number of logical partitions, because the disk uses 4096 byte sectoring, yet is still small enough for MBR to still work. I would probably create 3 primary partitions, and then keep the rest of the drive in an extended partition and create logical partitions within it and see if that suffices.

Second, although I'd like to use GPT so as to be able to arbitrarily add additional partitions, it appears that I could do the same thing using MBR and LVM. I'm not that familiar with LVM (although I worked with a couple of similar products a few years ago under a commercial UNIX product, so I'm familiar with the concepts) - a moderate learning curve is looming!

Third, I did attempt, using fdisk, to make the GPT "partition" bootable, but I was still unable to write a GRUB2 boot block to it (or if I did succeed, it wasn't evident as I still couldn't boot it, nor even get a GRUB> prompt!). 

Fourth, I'm not inclined to try a virtual machine for now, but will if nothing else seems to work. I just increased my memory from 2 to 4GB, and that's as far as I can take it with this laptop. The BIOS is reasonably current - it's one rev behind, for a battery power reporting problem under Windows - and this box will never be able (according to HP) to run Windows 7. It wasn't clear as to exactly why, but I suspect the lack of EFI support may be a factor.

Fifth, I could also try to set up a boot stanza under my current openSUSE 11.4 set-up (and, perhaps, set up a directory under its root partition to hold the files needed to boot the 3TB drive). However, I'm concerned that the legacy GRUB 0.97 might not react properly - drive ordering has always been, um, interesting when plugging in a bootable USB drive and some distros still don't sort it all out correctly, requiring manual intervention (editing of menu.lst) to correct the drive/partition numbering.

Since none of the "data" currently sitting on this drive is important - i.e., it's just a scratch/sandbox disk - I'm leaning in favor of starting from scratch and repartitioning with MBR and see if the 4096 byte sectoring is the root cause of my problem. But, if anyone has any further observations, I'd appreciate them. If I get that working, then I'll look again at GPT partitioning and see if there's a bug lurking or if we need to document an installation restriction or something. I'm playing with this in between a number of other projects at home, so there's no particularly critical timeframe, at least from my perspective. My thanks to Rod and others for their patient help!

---

### Post by srs5694 on 2011-09-15
> **brc816 said:**
> Fifth, I could also try to set up a boot stanza under my current openSUSE 11.4 set-up (and, perhaps, set up a directory under its root partition to hold the files needed to boot the 3TB drive). However, I'm concerned that the legacy GRUB 0.97 might not react properly - drive ordering has always been, um, interesting when plugging in a bootable USB drive and some distros still don't sort it all out correctly, requiring manual intervention (editing of menu.lst) to correct the drive/partition numbering.

If you can put the Ubuntu kernel and initial RAM disk on your laptop's internal disk, then GRUB's quirks with respect to drive ordering evaporate. This is because GRUB's job is to load the kernel, load the initial RAM disk, and execute the kernel. Once the kernel is running, it's the kernel that's in charge of the rest, including locating its root (/) partition. Thus, if the root (/) partition is on the USB drive but the kernel and initial RAM disk are on an internal disk, GRUB doesn't need to know a thing about the USB drive.

One caveat: If the BIOS becomes confused about drive ordering when you plug in the USB drive, then all bets are off. This is because the BIOS does its thing before GRUB, and GRUB actually relies on BIOS calls to load the kernel and the initial RAM disk. You might be able to work around such a problem by fiddling with BIOS settings, though. In fact, configuring the BIOS so that USB devices are *not* bootable might fix the problem!

---

### Post by brc816 on 2011-09-16
Hmmm... that IS a very interesting idea.

I'm assuming, however, that I'll have to use stitch in the correct parameters to the kernel and initrd lines, which I'll cut-n-paste from Oneiric's grub.cfg.

Here's my current, working, unadulterated /boot/grub/menu.lst on my openSUSE 11.4 installation that uses two internal 80GB Toshiba SATA hard drives:
```

# more /boot/grub/menu.lst
# Modified by YaST2. Last modification on Thu Aug 25 16:49:28 EDT 2011
# THIS FILE WILL BE PARTIALLY OVERWRITTEN by perl-Bootloader
# Configure custom boot parameters for updated kernels in /etc/sysconfig/bootloader

default 0
timeout 8
gfxmenu (hd1,1)/boot/message

###Don't change this comment - YaST2 identifier: Original name: linux###
title Desktop -- openSUSE 11.4 - 2.6.37.6-0.7
    root (hd1,1)
    kernel /boot/vmlinuz-2.6.37.6-0.7-desktop root=/dev/disk/by-id/ata-TOSHIBA_MK8034GSX_Y6SIT3WMT-part2 resume=
/dev/disk/by-id/ata-TOSHIBA_MK8034GSX_Y6SIT3WMT-part1 splash=silent quiet showopts nomodeset vga=0x348
    initrd /boot/initrd-2.6.37.6-0.7-desktop

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe -- openSUSE 11.4 - 2.6.37.6-0.7
    root (hd1,1)
    kernel /boot/vmlinuz-2.6.37.6-0.7-desktop root=/dev/disk/by-id/ata-TOSHIBA_MK8034GSX_Y6SIT3WMT-part2 showopt
s apm=off noresume edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 nomodeset x11failsafe vga=
0x348
    initrd /boot/initrd-2.6.37.6-0.7-desktop

###Don't change this comment - YaST2 identifier: Original name: windows 1###
title windows 1
    rootnoverify (hd0,0)
    chainloader +1

###Don't change this comment - YaST2 identifier: Original name: windows 2###
title windows 2
    rootnoverify (hd0,1)
    chainloader +1


```

So, I think I'll plan on creating a "/boot/Seagate" on my openSUSE 11.4 disk to house the kernels and initrd's for Oneiric (and, perhaps, others distros later) and then add something like this to my existing /boot/grub/menu.lst:
```

title OneiricTest -- Ubuntu, with Linux 3.0.0-11-generic on 3TB
    root (hd1,1)
    kernel /boot/Seagate/vmlinuz-3.0.0-11-generic root=/dev/disk/by-id/81c7c0e8-4e69-4d8b-ab19-d9cf3a97c065 ro nomodeset noresume
    initrd /boot/Seagate/initrd.img-3.0.0-11-generic
```

But, I am having problems with the exact semantics since I'd be using Legacy Grub (0.97), but grabbing a kernel that might or might not identify its disks as "/dev/disk/by-id/". Clearly, I'll be augmenting the exact kernel arguments (although, for now, 'nomodeset' is an absolute requirement!), and will want to specify the swap partition on the 3TB spindle for the 'resume' clause. (Chainloading directly to the GRUB2 stuff on the 3TB would be wonderful, but I don't think legacy GRUB will let me).

---

### Post by brc816 on 2011-09-16
SUCCESS !  (BUT, I'm not going to mark it as 'SOLVED' quite yet, but it's looking good).

My initial attempt to boot using the semantics in my previous reply failed, with initramfs "giving up - unable to find root" and dropping to its (quite limited) shell. When poking around, I discovered that initram saw various "devs", including "sdc7", "sdc3", etc. This solved my semantics problem - I re-edited my menu.lst:

```
##Added manually 16 Sep 2011 1005EDT
title OneiricTest -- Ubuntu, with Linux 3.0.0-11-generic on 3TB
    root (hd1,1)
    kernel /boot/Seagate/vmlinuz-3.0.0-11-generic root=/dev/sdc7 ro nomodeset resume=/dev/sdc3
    initrd /boot/Seagate/initrd.img-3.0.0-11-generic
```

Note that I had already created the ad-hoc "/boot/Seagate" directory on my openSUSE platter, and copied the contents of the Oneiric /boot (but NOT /boot/grub) directory to it:

```

-rw-r--r-- 1 root root   730507 Sep  2 15:29 abi-3.0.0-10-generic
-rw-r--r-- 1 root root   730434 Sep 14 00:53 abi-3.0.0-11-generic
-rw-r--r-- 1 root root   730234 Aug 30 11:52 abi-3.0.0-9-generic
-rw-r--r-- 1 root root   134703 Sep  2 15:29 config-3.0.0-10-generic
-rw-r--r-- 1 root root   134703 Sep 14 00:53 config-3.0.0-11-generic
-rw-r--r-- 1 root root   134769 Aug 30 11:52 config-3.0.0-9-generic
-rw-r--r-- 1 root root 13736410 Sep 13 20:28 initrd.img-3.0.0-10-generic
-rw-r--r-- 1 root root 13736703 Sep 14 22:56 initrd.img-3.0.0-11-generic
-rw-r--r-- 1 root root 13736497 Sep  5 16:08 initrd.img-3.0.0-9-generic
-rw-r--r-- 1 root root   176764 May  2 19:07 memtest86+.bin
-rw-r--r-- 1 root root   178944 May  2 19:07 memtest86+_multiboot.bin
-rw------- 1 root root  2694141 Sep  2 15:29 System.map-3.0.0-10-generic
-rw------- 1 root root  2694177 Sep 14 00:53 System.map-3.0.0-11-generic
-rw------- 1 root root  2692451 Aug 30 11:52 System.map-3.0.0-9-generic
-rw------- 1 root root     1367 Sep  2 15:30 vmcoreinfo-3.0.0-10-generic
-rw------- 1 root root     1367 Sep 14 00:58 vmcoreinfo-3.0.0-11-generic
-rw------- 1 root root     1366 Aug 30 11:54 vmcoreinfo-3.0.0-9-generic
-rw------- 1 root root  4657904 Sep  2 15:29 vmlinuz-3.0.0-10-generic
-rw------- 1 root root  4658672 Sep 14 00:53 vmlinuz-3.0.0-11-generic
-rw------- 1 root root  4654192 Aug 30 11:52 vmlinuz-3.0.0-9-generic
```
By doing all this, I was able to boot Oneiric just fine.

It's a hack - an ugly hack - but it appears to be working for now. It's ugly because every time Oneiric upgrades its kernel giblets, I'll have to manually recopy them over to my openSUSE /boot/Seagate directory and re-edit menu.lst. It also means that I really should move them down to a new /boot/Seagate/Oneiric directory (and amend menu.lst appropriately) so that if I chose to plop Fedora 16, Mageia 2.0, and/or openSUSE 11.4 onto my 3TB for testing, I can.

It doesn't test GRUB2 (be it Oneiric's sub-version or Fedora 16's, for example), but that'll give me something to tinker with later on. But, for now, I can boot Oneiric off of the 3TB drive,
and was able to log in.

Thank you, Rod !! :KS

---

### Post by srs5694 on 2011-09-16
Another option you might consider, which would work more smoothly in the long run, is to create separate /boot partitions on the internal drive for each distribution you plan to install. That way, their regular boot loader maintenance scripts should be able to take care of updates and whatnot. You'll need to decide which OS's boot loader resides in the MBR, and therefore controls the overall boot process. That boot loader could either chainload to the other boot loaders or it could boot the other distributions directly (similar to what you've just configured).

---

### Post by brc816 on 2011-09-16
Yes, I agree that would be the way to go, but as it stands now, each of the two internal hard drives are "only" 80GB apiece, and I'm rather reluctant to re-do my working system. If I were re-installing it from scratch, I'd be using much bigger platters and would have plenty of room to do that. The fact that I had no trouble booting off of a 4096-byte sector disk with a GPT on it is quite heartening, however, considering I'm using Legacy GRUB and a "legacy" BIOS with no (U)EFI capabilities! 

I did copy the Oneiric files down to /boot/Seagate/Oneiric, and that worked just fine. I was going to do the same with the openSUSE 12.1M3 and Fedora16 pre-Beta installations, only I discovered that they were munged by all of my other thrashing around - the /boot directories were empty. So, I'm going to re-install those distros, and we'll see what happens.

---

### Post by srs5694 on 2011-09-16
> **brc816 said:**
> Yes, I agree that would be the way to go, but as it stands now, each of the two internal hard drives are "only" 80GB apiece, and I'm rather reluctant to re-do my working system.

That's understandable, but I do want to point out that /boot partitions can be pretty small, even by the standards of an 80 GB hard disk. Mine are typically about 200 MB, so it'd take five of them to consume even 1/80th of the disk's capacity.

Another option might be to use a bootable USB flash drive, particularly if you're not hurting for lack of USB ports. I gather there are some pretty low-profile USB flash drives available.

Of course, these are just possibilities. If you're happy with the way it's working, sticking with it makes sense. ("If it ain't broke, don't fix it," as they say.) I'm just tossing out thoughts since you said you were concerned about having to manually intervene when Ubuntu updates its kernel.

> If I were re-installing it from scratch, I'd be using much bigger platters and would have plenty of room to do that. The fact that I had no trouble booting off of a 4096-byte sector disk with a GPT on it is quite heartening, however, considering I'm using Legacy GRUB and a "legacy" BIOS with no (U)EFI capabilities!

UEFI support is certainly not required to use GPT. I've got several BIOS-based computers that use GPT exclusively. Since you're now booting the kernel off your internal MBR disk, you don't even need GPT support in GRUB; GRUB has done its thing and terminated by the time the kernel needs to read the GPT disk.

> I did copy the Oneiric files down to /boot/Seagate/Oneiric, and that worked just fine. I was going to do the same with the openSUSE 12.1M3 and Fedora16 pre-Beta installations, only I discovered that they were munged by all of my other thrashing around - the /boot directories were empty. So, I'm going to re-install those distros, and we'll see what happens.

Good luck with that!

---

### Post by brc816 on 2011-09-18
I agree that adding unique /boot partitions might do the trick, but the problem is, I think I'd have to completely re-partition my second 80GB (Linux) disk and that's a really scary prospect:

```
# fdisk /dev/sdc -l

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xde462e57

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63     4209029     2104483+  82  Linux swap / Solaris
/dev/sdc2         4209030    46154744    20972857+  83  Linux
/dev/sdc3        46154745   156296384    55070820   83  Linux

```

I did try with a 16GB thumbdrive a while ago, as I have a Natty system built onto it - yes, it's extremely slow - but that didn't seem to work, either, at the time. I think I'll give it another try today or tomorrow to see if what I've learned from my other poking around has any effect.

In the meanwhile, I've managed to re-install Fedora 16 pre-Beta and openSUSE 12.1 Milestone 5 onto each of their own partitions on the 3TB drive and can boot them at will from my main openSUSE 11.4 GRUB menu after copying the /boot directories from each of them over to /boot/Seagate/<os name> and adding appropriate stanzas to my primary menu.lst:
```

###Added manually 16 Sep 2011 1005EDT
title OneiricTest -- Ubuntu, with Linux 3.0.0-11-generic on 3TB Partition 7
    root (hd1,1)
    kernel /boot/Seagate/Oneiric/vmlinuz-3.0.0-11-generic root=/dev/sdc7 ro nomodeset resume=/dev/sdc3 vga=0x348
    initrd /boot/Seagate/Oneiric/initrd.img-3.0.0-11-generic                                                    
                                                                                                                
###Added manually 17 Sep 2011 1040EDT                                                                           
title Fedora 16 Beta on 3TB partition 4                                                                         
    root (hd1,1)                                                                                                
    kernel /boot/Seagate/Fedora16/vmlinuz-3.1.0-0.rc6.git0.3.fc16.x86_64 root=UUID=c958f578-d90f-4c87-82d1-718ae
d946b6a ro nomodeset rhgb quiet vga=0x348 raid=noautodetect resume=UUID=a4c9ac84-1e2e-4158-a6bb-cc73c035b358
    initrd /boot/Seagate/Fedora16/initramfs-3.1.0-0.rc6.git0.3.fc16.x86_64.img

###Added manually 17 Sep 2011 1525EDT
title openSUSE 12.1 Milestone 5 on 3TB Partition 5
    root (hd1,1)
    kernel /boot/Seagate/OpenSUSE121/vmlinuz-3.0.0-4-desktop root=/dev/disk/by-uuid/57c89500-8857-48bb-8588-b900
904a9d57 nomodeset resume=/dev/disk/by-id/ata-ST3000DM001-9YN166_Z1F0116P-part3 splash=silent quiet showopts vga
=0x348
    initrd /boot/Seagate/OpenSUSE121/initrd-3.0.0-4-desktop

```

So, yes, now I can go "play" with these distros. BUT, I can see that Legacy GRUB is quite adamant about not letting me add a third disk to the mix so that I can chainload to it. I've tried various adjustments to the device.map to no avail. (It was interesting to see that openSUSE 12.1 uses Legacy GRUB and a 3.0 kernel that gives a slightly different different string under /dev/disks/by-id from oS 11.4 and its 2.6 kernel, BTW). Ideally, I'd prefer to be able to have one short stanza that would permit me to jump over to the Seagate drive and bring up someone's (preferably Ubuntu's) GRUB2 menu and then select my test distros from there. It's what I've been doing for a year on my single-internal-hard-disk Acer Aspire Netbook, but no luck here so far.
I'm suspicious that may be due to the 4096 byte sectoring, but I can't prove it yet, nor can I prove that anyone's successfully scribbled a GRUB(2) boot block on the 3TB drive, either.

---

### Post by oldfred on 2011-09-18
I find it interesting that openSUSE uses the disk by ID style. I think that then avoids the issues I have with chain loading.

I have one small 160GB drive I converted to gpt to learn about it, and I have 3 drives and several flash drives that I can boot from.

I found with Ubuntu's grub2 that whatever drive I boot from it is hd0, and if booting into the gpt drive I need the (hd1,gpt2) style for gpt partitions or from the gpt into the MBR (hd3,msdos12). So when I chainload to another hard drive's MBR my standard 40_custom is really only correct when booted from one drive as the drive numbers change if I use the smae 40_custom on installs in another drive.  Or when I boot sdc it is hd0, sda is hd1 etc. 

The newest grub 1.99 now uses /dev/sda as an alternate to hd0, but we have seen users where the BIOS does not always bring drives up in the same order.

---

### Post by brc816 on 2011-09-18
Hi, Fred ! ):P

Well, what was interesting was that openSUSE's /dev/disk/by-id changed (is changing?) between 11.4 and 12.1, in that 11.4 called everything /dev/disk/by-id/ata-mumble, even my USB drives. In 12.1Mx, the USB drive is /dev/disk/by-id/USB-mumble. So, that was confusing enough...

But, since I last posted a few hours ago, I tried my Natty 16GB thumbdrive, and managed to boot the 3TB's distros, but only through the /boot copies I plopped on my hard drive. And, in trying to chase that down a bit further, I'm discovering that the "UUIDs" aren't as Universal as I'd hoped. And since GRUB2 looks at all of the menu.lst's and grub.cfg's it can, it's starting to get a bit confusing.

FYI, my current Natty 16GB thumbdrive is partitioned using MBR/MSDOS partitioning, and basically a 700MB swap partition and the rest as the root partition, and the latter is only about 25% used. I'm going to set up another 16GB Natty thumbdrive, but will use Rod's suggestion and add a bunch of small (~100MB) partitions to use as /boot for the various distros on the 3TB.
(I plan to use MBR and MSDOS partitions on the 'new' thumbdrive).

That still won't clarify why I can't seem to scribble a cogent boot block on the 3TB drive - it may yet be a 4096 byte sector issue as Fedora 16 pre-Beta's 'grub2-mkconfig' complained - but at least I will be able to dd the first 512 bytes or whatever to a regular file and compare/examine it.

---

### Post by oldfred on 2011-09-18
I have not had to deal with very large drives and 4096 sectors. But Rod sold me on gpt so I converted one older drive. I also just as a test used gpt on my 16GB install. I still created a bios-grub, 8GB for the install and the rest is just for data, but not really used. I have no swap but with 4GB of RAM it works ok. I changed a lot of settings to reduce writes.

I have so many copies of Ubuntu installed I have to turn off os-prober and use my 40_custom to minimize entries and add spacers.

---

### Post by brc816 on 2011-10-01
My apologies to Rod and Fred for being blatantly absent for the last week after they took the time to respond to me.

I was off trying to see if the Fedora 16 pre-Beta kits would fare any better and the answer appears to be they aren't.

I've pretty much come to the conclusion that the real issue is that Legacy Grub (0.97) and GRUB2 (1.99) both are designed/built with just 512 byte sectors in mind. I haven't studied the code of either of them yet, and my speculation could be way off base, but it appears that they each provide JUST a 512 byte boot block that's scribbled into the very first sector (call it "MBR" for now) of either the spindle (e.g., /dev/sdc) or the user-requested boot partition (e.g., /dev/sdc2). OK, fine, but I don't know what happens when it hits byte #513 assuming we actually DID write something into the first 512 bytes of the 4096 available.

In other words, until GRUB2 is re-designed/re-written to provide a 4096-byte boot block (and, obviously, other related files that would be affected by whatever design changes to the boot block are made), it's unlikely (IMNSHO, anyway) that we'll ever be able to boot off of the hardware that I specified in my OP. I'm well aware that that would not be a trivial task by any standard.

In the meanwhile, I do applaud Rod for his suggestion that I copy over the /boot directory to my primary system and boot through it. It's been working fairly well for me so far. I'm looking into simplifying it (i.e., just pointing the menu.lst stanza to execute core.img), but that's a work-in-progress.
With 2 new Betas coming out this week (openSUSE 12.1 and Fedora 16), plus the Oneiric Beta to re-install and try again, I'm going to be fairly busy!

Obviously, if my assumptions/speculations are erroneous, I'd appreciate the feedback - it's been a steep learning curve for me.

Thank you!!

---

### Post by oldfred on 2011-10-01
Thanks for the update.

I did find that a user with efi boot and 4k did work, see this bug report from Jan, 2011 that was fixed. 
His fdisk showed this:
> Sector size (logical/physical): 512 bytes / 4096 bytes

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/702707](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/702707)

---

### Post by brc816 on 2011-10-02
Hmmm - interesting. I need to study that and see *why*, but my suspicion is that it worked because he had an EFI-capable BIOS, which my HP dv9000z does not. (My 32-bit Acer Aspire netbook does, and boots a 1TB/512byte-sector WD Book drive very nicely - it's the behaviour that I was hoping for with the 3TB/4096-byte sector drive.)

The comments in that bug about missing device.map file(s) is also interesting - I've seen that kind of behaviour lately, too. I think it was on Oneiric, and I'm pretty sure I saw it on Fedora16 Alpha as well. I'll see if I can reproduce it later this week.

Thank you for the link to that bug, though - TBH, I haven't made an exhaustive search of Ubuntu's GRUB bugs yet.

---

