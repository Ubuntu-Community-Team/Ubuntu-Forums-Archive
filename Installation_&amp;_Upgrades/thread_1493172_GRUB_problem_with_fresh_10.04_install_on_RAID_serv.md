---
title: "GRUB problem with fresh 10.04 install on RAID server"
date: 2010-05-25
forum: Installation &amp; Upgrades
---

### Post by tehschulman on 2010-05-25
My server is partitioned using software RAID in the following way:

40GB RAID1 root partition at /dev/md0
4.5TB RAID5 /home partition at /dev/md1

The other day I decided to upgrade my machine from 8.10 to 9.10 in the hopes of doing a second upgrade to 10.04 later. The upgrade to 9.10 seemingly went fine but once I attempted the 10.04 upgrade my server rebooted after it finished installing the downloaded packaged (skipping the clean up and finalizing steps in the prompt). 

When I turn on my system now I can successfully boot with GRUB (into a broken environment, but that's another story), but GRUB only gives me the option of booting into kernels from my 9.10 upgrade. Trying to modify the boot lines and booting into kernel 2.6.32-22-server, which exists on my /boot partition along with updated menu.lst files that include entries to these kernels, return a "File not Found" error.

Now after doing a fresh install of 10.04 using the LiveCD image, mounting the /dev/md0 and /dev/md1 and installing mdadm before the install and setting the MBR on /dev/md0, I am still greeted by the same exact GRUB boot choices from my 9.10 install.

Obviously the issue has to do with the MBR and the fact that I can't seem to point the bootloader to the right boot record, but my knowledge about RAID is somewhat limited and I need some advice on how to fix this issue. Thanks!

---

### Post by tehschulman on 2010-05-25
Really, no one can help me? I've reinstalled my system three times today trying to get the bootloader installed in the correct place but I'm still running into this issue.

---

### Post by tgalati4 on 2010-05-25
Perhaps I'm mistaken, but I don't think you can put /boot on a RAID partition.  Normally you have a small, normal boot partition (ext3) that the bootloader can read.  Once the bootloader has loaded the initrd image and starts to load the kernel, then the md devices are enumerated.

---

### Post by tehschulman on 2010-05-25
People advise against having your /boot partition on your root array, but you can still install GRUB into a master boot record on the disk and boot it (it worked fine when I first set my server up). The real problem occurs when you screw your system up like I've done and you're trying to recover things.

Currently I have a LiveCD of 10.04 running and have successfully chrooted into my system. I'm trying to mount my /home partition (which is encrypted with ecryptfs) and have been looking around for some good instruction on how to install and set up GRUB with my current conditions.

Is there a simple way for me to erase the mbr that the screwy install of GRUB is on and reinstall GRUB from the LiveCD? From the looks of my disks /dev/sda1 is the only partition with a bootable flag but attempting to use /dev/sda1 as my mbr in the most recent install of 10.04 has proved unsucessful.

I just wish I knew where this defunct bootloader exists on my disks and how I can get it to point to the proper /boot folder.

---

### Post by tehschulman on 2010-05-26
Ok, so I did some searching and found how to see which partition has the GRUB stage1. It turns out that both (hd0,0) AND (hd1,0) have entries for stage1. I assume that maybe the bootloader is defaulting to the entry on (hd1,0) and since I have never explicitly set up my bootloader on (hd1,0) this is why I'm getting the old kernel menu when I boot up.

So my question is really how can I remove the stage1 entry from (hd1,0)? Is it a problem if both of these disks have entries? I'm hesitant to run 

```

grub> root (hd1,0)
grub> setup (hd1)

```

but it would probably fix the issue.

---

### Post by tgalati4 on 2010-05-26
Or you can use the GRUB map command to remap the drives.  I've used it in the past to repair a complicated GRUB installation when moving drives and distros around.

Search the forums for (grub map) for some examples.

---

### Post by tehschulman on 2010-05-26
There doesn't appear to be a device.map file in my /boot/grub directory. I did find some info on the map command however and ran:

```

grub> map (hd0) (hd1)

```

That basically mirrors the map information from hd0 to hd1 right? I also came across some info for using the dd command to overwrite the mbr on the second disk. Would this be useful for my purposes? I am trying to recover the second disk (md1) as we speak so I'm wary of writing any info to it. Also for reference, here is my fdisk -l:

```

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00035f85

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4863    39062016   fd  Linux raid autodetect
/dev/sda2            4864      182401  1426073985   fd  Linux raid autodetect

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009cb04

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4863    39062016   fd  Linux raid autodetect
/dev/sdb2            4864      182401  1426073985   fd  Linux raid autodetect

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000717dc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        4863    39062016   fd  Linux raid autodetect
/dev/sdc2            4864      182401  1426073985   fd  Linux raid autodetect

Disk /dev/sdd: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00053c20

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        4863    39062016   fd  Linux raid autodetect
/dev/sdd2            4864      182401  1426073985   fd  Linux raid autodetect

Disk /dev/md0: 40.0 GB, 39999438848 bytes
2 heads, 4 sectors/track, 9765488 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

Disk /dev/md1: 4380.9 GB, 4380899082240 bytes
2 heads, 4 sectors/track, 1069555440 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 196608 bytes
Disk identifier: 0x00000000

Disk /dev/md1 doesn't contain a valid partition table

```

---

### Post by tgalati4 on 2010-05-26
The map command simply overrides (temporarily) what is laid out in the device.map file.  Mine looks simple (on a laptop with one disk):

tgalati4@tpad-Gloria7 /boot/grub $ cat device.map
(hd0)	/dev/sda

You can also edit the device.map file and keep trying partitions until grub finds an appropriate boot loader.  The interactive map command is sometimes easier, but make a written map of your partitions so you can mark them off as you try them.

The map command is also useful for dual-booting windows when a windows disk was moved to something other than the first partition on the first disk (/dev/sda1).

You can use the root and setup commands that you listed previously to overwrite the MBR.  You just need to make certain that you are setting up the correct devices.

For instance, you can install the GRUB bootloader to any MBR on any disk and you can install the /boot/grub (stage2 binaries) to any partition.  Then the GRUB configuration can point to the kernel on any disk.  This concept trips people up.  It allows extreme flexibility (hence the name Grand) but makes troubleshooting difficult.

Your initial problem could simply be your grub configuration was using older /dev/sda1 notation when Lucid now uses UUID notation to enumerate partitions.

---

### Post by tehschulman on 2010-05-26
Alllll righty. Created a device.map with GRUB, it outputs the following:
```

ubuntu@ubuntu:/boot/grub$ cat device.map
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
(hd3)	/dev/sdd

```

I attempted the map to (hd3) (the only other bootable partition on my setup) and it seemed to work ok, but rebooting still brings me to the same damn GRUB menu. Trying to setup GRUB on (hd3) fails since apparently there is no bootloader installed on /dev/sdd despite it being flagged as boot:

```

grub> root (hd3,0)
root (hd3,0)
grub> setup (hd3)
setup (hd3)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 15: File not found

```

Still scratching my head on this one. If I've reinstalled GRUB on the only place GRUB can be installed, (hd0). then where is GRUB pulling this old set of kernels from? I appreciate you trying to walk me though this tgalati4, hopefully we can solve it together.

---

### Post by tehschulman on 2010-05-30
Would it be safe to install the bootloader onto /dev/md1 (the partition that has info that I do not want to overwrite and am hesitant to make changes to for fear of data loss)?

I bought a 4.4TB external hard drive so I can back up my /home drive once I get a working system installed that can get booted properly. After I back it up I plan to do a full wipe and reinstall.

---

