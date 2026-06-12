---
title: "Dual Boot Windows 8 on SSD and Ubuntu on HDD"
date: 2013-06-10
forum: Installation &amp; Upgrades
---

### Post by squishysquashy on 2013-06-10
[h=5]I'm about to install Ubuntu on my Windows 8 Machine. I have the following setup:
 
 *Primary SSD with Windows 8 installation
 *Secondary HDD with empty partition ready for Ubuntu installation
 
I'll tell you what I plan to do, please can one of you experts give me a nod of agreement or let me know I'm about to make a major mistake![/h]I have a 97.6GB partition on my secondary HDD laid out for Ubuntu. I will use 10GB as a swap area (keeping it as a logical partition). The remaining space will be set as a primary partition, type ext4, and set the mount point as root. Will this be ok? Should I be setting the mount point as something else? My concern is that the boot loader won't find Windows, or booting from the secondary HDD will lead to a compromise in startup speed.

---

### Post by fantab on 2013-06-10
Sounds good.

However, you must tell us more about your machine. Did Win8 come preinstalled or did you installed it? How did you install it, I mean UEFI or BIOS?
Because you need some additional procedure if your Win8 came pre-installed or if you installed it in UEFI.

---

### Post by squishysquashy on 2013-06-10
Thanks fantab.

It came preinstalled with Windows 8. I'm at the installation screen now, not quite sure which I should choose for the "Device  for boot loader installation". I have /dev/sda which is my SSD and I  have dev/sdb which is my HDD. For some reason, "Windows 8 (loader)" is  at /dev/sdb1.

My ext4 partition is at /dev/sdb7. Do I select this device for my boot loader installation?

---

### Post by fantab on 2013-06-10
> **squishysquashy said:**
> It came preinstalled with Windows 8. I'm at the installation screen now, not quite sure which I should choose for the "Device  for boot loader installation". I have /dev/sda which is my SSD and I  have dev/sdb which is my HDD. For some reason, "Windows 8 (loader)" is  at /dev/sdb1.

My ext4 partition is at /dev/sdb7. Do I select this device for my boot loader installation?

If you are installing Ubuntu on /dev/sdb then bootloader, Grub must also go on /dev/sdb.

Pre-installed Windows8 mostly comes installed in UEFI mode... if that is the case then Ubuntu too must be installed in UEFI mode. For this you need to re-partition your HDD with GPT table as we cannot UEFI boot from 'msdos' table.

---

### Post by squishysquashy on 2013-06-10
I partitioned during the Ubuntu install, is that what you mean?

---

### Post by fantab on 2013-06-10
Nope. The partition table must be changed from 'msdos' to 'GUID'. Run Ubuntu Live DVD/USB and from it run the following command in the TERMINAL [Ctrl+alt+T]:

```
sudo parted -l
```

the output will tell us what partition table is on the HDD. If you have any doubts post the output here.

---

### Post by squishysquashy on 2013-06-10
Sure enough, the partition table says "msdos". (Although the ubuntu partition has a "linux-swap(v1)" file system)

What do I need to do? :)

---

### Post by fantab on 2013-06-10
Post the output of 'sudo parted -l', I need to see it to be able to guide you in the right direction.

---

### Post by oldfred on 2013-06-10
I have BIOS but use gpt. I have created my gpt partitions with gparted. Under device, create partition table, advanced, choose gpt not the default msdos (MBR) partitioning.

For more info on UEFI see also my signature. Some links to others with two drives and what they did.

      
 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 250 MB efi FAT32 (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB bios_grub no format (for BIOS boot not required for UEFI)
gpt or MBR(msdos)
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

You want an efi partition on sdb and I would put a copy of grub2's efi in that partition, but not sure how your UEFI will read both drives and offer to boot. You may also need grub2's efi boot files in the sda efi file. Either way you have to modify grub's chain load to Windows to boot the Windows file in the sda efi file. Boot-Repair was updated to handle that, but some have had to manually edit boot stanzas.

---

### Post by squishysquashy on 2013-06-10
Thank you, fantab. Here is the output- it shows first my primary drive with win8, then my secondary drive, then the liveusb for installation:

ubuntu@ubuntu:~$ sudo parted -l
Model: ATA KINGSTON SH103S3 (scsi)
Disk /dev/sda: 240GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  240GB  240GB  primary  ntfs


Model: ATA ST750LX003-1AC15 (scsi)
Disk /dev/sdb: 750GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  368MB  367MB   primary   ntfs            boot
 2      368MB   577GB  577GB   primary   ntfs
 3      577GB   682GB  105GB   primary   linux-swap(v1)
 4      682GB   750GB  68.2GB  extended                  lba
 5      682GB   750GB  68.2GB  logical   ntfs


Model: USB Mass Storage Device (scsi)
Disk /dev/sdc: 7948MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  7948MB  7947MB  primary  fat32        boot

---

### Post by squishysquashy on 2013-06-10
oldfred, is there any alternative to what you've said? Going to "device > create partition table > advanced" warns me that I'll erase my whole disk, but I've got 208GB of music and games there already!

---

### Post by fantab on 2013-06-10
Okay, your Windows 8 is NOT installed in UEFI mode. We don't have to change anything. However, your HDD /sdb partitioning is confusing.

> 3      577GB   682GB  105GB   primary   linux-swap(v1)
 4      682GB   750GB  68.2GB  extended                  lba
 5      682GB   750GB  68.2GB  logical   ntfs

Why do you have a 105GB SWAP?
What is the 5th partition for?

---

### Post by squishysquashy on 2013-06-10
So I can go right ahead and install it? :)

Was hoping to install a third OS on that partition in the future, given up on that idea for now though!

---

### Post by fantab on 2013-06-10
You have fix those partitions first.

Delete the partitions 3,4 and 5 with **Gparted** from Ubuntu LiveDVD/USb. Go to windows and 'shrink' the /dev/sdb2 and create some more GB if its possible.

Recreate them as:
/dev/sdb3 25GB Primary formatted with EXT4 for Ubuntu main mountpoint=/
/dev/sdb4 All the Remaing GB EXTENDED
/dev/sdb5 4GB LOGICAL SWAP
/dev/sdb6 25GB LOGICAL for third future OS
/dev/sdb7 all the remaining GB Logical /home (to store your Ubuntu DATA like Documents, Music etc.)

---

### Post by squishysquashy on 2013-06-10
I quit halfway through something, then came back to it, had somehow created a 105GB swap. In reality it will be 10GB swap, 95GB ext4, and I am partitioning using the Ubuntu installer/

---

### Post by squishysquashy on 2013-06-10
And just to confirm, am I ok to install boot loader at /dev/sdb7 or does it need to be something else, e.g. /dev/sdb?

---

### Post by fantab on 2013-06-10
See post #14, I edited it.

You have to install Boot Loader Grub on **/dev/sdb only** not on /dev/sdb7.

---

### Post by squishysquashy on 2013-06-10
Thank you so much, fantab! Everything is now installed and appears to be working perfectly :)

---

