---
title: "Dual Booting: Remove Partition"
date: 2012-06-03
forum: Installation &amp; Upgrades
---

### Post by cozski on 2012-06-03
I have dual boot set up on my Laptop. I was running Jolicloud and recently installed Zorin (both ubuntu based distros). I've decided to go with Zorin and completely remove Jolicloud. How do I do this? I installed both from LiveCD after creating image from their own website distros. Here's the output from sudo fdisk -l. Thanks in advance.

luther@luther-Satellite-L300:~$ sudo fdisk -l
[sudo] password for luther: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00013dc6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   172419832    86208892+  83  Linux
/dev/sda2       172421118   312580095    70079489    5  Extended
/dev/sda5       300564480   312580095     6007808   82  Linux swap / Solaris
/dev/sda6       172421120   296392703    61985792   83  Linux
/dev/sda7       296394752   300560383     2082816   82  Linux swap / Solaris

Partition table entries are not in disk order
luther@luther-Satellite-L300:~$ sudo fdisk -l

---

### Post by wilee-nilee on 2012-06-03
> **cozski said:**
> I have dual boot set up on my Laptop. I was running Jolicloud and recently installed Zorin (both ubuntu based distros). I've decided to go with Zorin and **completely remove Jolicloud. How do I do this?** I installed both from LiveCD after creating image from their own website distros. Here's the output from sudo fdisk -l. Thanks in advance.

luther@luther-Satellite-L300:~$ sudo fdisk -l
[sudo] password for luther: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00013dc6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   172419832    86208892+  83  Linux
/dev/sda2       172421118   312580095    70079489    5  Extended
/dev/sda5       300564480   312580095     6007808   82  Linux swap / Solaris
/dev/sda6       172421120   296392703    61985792   83  Linux
/dev/sda7       296394752   300560383     2082816   82  Linux swap / Solaris

Partition table entries are not in disk order
luther@luther-Satellite-L300:~$ sudo fdisk -l

Very confusing you say you have removed it then ask how.

Make sure zorin has the boot control, and remove joli with a gparted. You also have 2 swaps you need only one.

Boot control means that zorins bootloader is in the MBR.

If you want to resize anything, use a live cd with gparted, really a live cd would be best with the whole process.

---

### Post by Ron O on 2012-06-03
Similar Issue- running Ubuntu 10.04 and plan to install latest Ubuntu or probably Mint on a separate partition, keeping 10.04 until the new OS is all tweaked. Then I plan to reformat the old 10.04 partition and add it on to the new partition with GParted live CD. as I've done sucessfully in the past.

I am assuming there will be 2 Grub installations, one on the old 10.04 partition that is now being used (and will go away) and one on the newly installed partition   

My question is once both versions are installed, how do I know which GRUB will be operative- the one on the newly installed OS partition or the one on the old 10.04 partition? What I am trying to avoid is being locked out of the system when I reformat the 10.04 partition, which will delete that Grub installation entirely. How will I get the system to boot to the GRUB on the new partition?

---

### Post by wilee-nilee on 2012-06-03
> **Ron O said:**
> Similar Issue- running Ubuntu 10.04 and plan to install latest Ubuntu or probably Mint on a separate partition, keeping 10.04 until the new OS is all tweaked. Then I plan to reformat the old 10.04 partition and add it on to the new partition with GParted live CD. as I've done sucessfully in the past.

I am assuming there will be 2 Grub installations, one on the old 10.04 partition that is now being used (and will go away) and one on the newly installed partition   

My question is once both versions are installed, how do I know which GRUB will be operative- the one on the newly installed OS partition or the one on the old 10.04 partition? What I am trying to avoid is being locked out of the system when I reformat the 10.04 partition, which will delete that Grub installation entirely. How will I get the system to boot to the GRUB on the new partition?

Couple of ways to make sure the OS you want to keep has the grub control=that grubs in the mbr.

A regular install should put its grub to the mbr, so the last install should have the control. What ever OS is first in the grub menu has control if you have not modified grub.

You can easily though control this. With a install, in the install phase use the something other option, there is a where grub is put option.

From a install itself in ubuntu or mint to set that as the controlling boot the command is from the desktops terminal.

```
sudo grub-install /dev/sdX
```X is the HD (mbr), for example if you run this command.
```
sudo fdisk -lu
```You get the partitions listed, the mbr is not a partition, just the first three letter like sda, sdb , sdc...etc, so if you see sda with the earlier command, the  command is.
```
sudo grub-install /dev/sda
```Always run this command after loading the mbr or with any changes to grub.
```
sudo update-grub
```

---

### Post by Ron O on 2012-06-04
Thanks. Sounds pretty manageable  to me.

After this new LTS release, I won't have to do this again for FIVE years. Yipee!

---

