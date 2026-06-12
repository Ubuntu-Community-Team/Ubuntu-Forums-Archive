---
title: "installed 14.04 on new SSD and now can't boot in to it"
date: 2014-06-25
forum: Installation &amp; Upgrades
---

### Post by visctrix on 2014-06-25
The BootInfo report link is [http://paste.ubuntu.com/7702528/](http://paste.ubuntu.com/7702528/)

When I try to boot from the SSD, I eventually get the message:[INDENT]
Gave up waiting for boot device. Common problems:
[snip]
ALERT! /dev/disk/by-uuid/6ef4e90b-6867-4f41-ac23-afa6ace6fdfe does not exist.
Dropping to a shell!

[/INDENT]
Then I get the BusyBox shell (ash)

Thanks for any advice

Henry

---

### Post by papibe on 2014-06-25
Hi m-henry.

I recommend repairing grub (boot tool) using Boot-Repair. Here's a [tutorial]("https://help.ubuntu.com/community/Boot-Repair").

Hope it helps. Let us know how it goes.
Regards.

---

### Post by visctrix on 2014-06-25
Cheers papibe

I did that first before posting here.

---

### Post by oldfred on 2014-06-25
Do you have AHCI on in BIOS?
Does BIOS correctly see drive? It should have or else it would not have installed.

I do not like Boot-Repairs autofix with more than one drive as it just installs one grub to every MBR. Better to use advanced mode and have each drive have the boot loader for the install in that drive. Then if one drive has issues, you may be able to boot from other drive.

Are you using nomodeset in grub menu to boot? You probably need to also install the nVidia proprietary drivers.
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by visctrix on 2014-06-25
Thanks oldfred

1. I can't find any reference to AHCI in my BIOS. I'd guess that it was standard in the Intel H87 chipset as it's Intel technology (as I've just learned from Wikipedia), but so far my searches haven't turned up anything that can confirm this (or anything else helpful).

2. BIOS does see the SDD, and I can set it to boot from there. I set the boot mode to LEGACY+UEFI and Boot Option #1 to Hard Disk: Samsung SSD 840 EVO 120G.

3. So far from my reading I'm assuming I can ignore EFI as I only have Ubuntu installed on the disk.

4. Before I started installing Ubuntu I read that I should use GPT for an SSD, but when I run sudo parted -l in a terminal it tells me that the partition table for the SSD is msdos (must have been done by the Ubuntu installer...)

---

### Post by visctrix on 2014-06-25
Whoops. I did also boot using NOMODESET but to no avail.

I can't see it being a graphics driver problem...?

I have been using another SSD as my root drive but there seemed to be a problem with the controller and it was taking ages to start processes. At least it let me boot up though

---

### Post by visctrix on 2014-06-25
[FONT=arial]How about this: [https://oldpapyrus.wordpress.com/tag/detect-ahci-enabled-bios-linux/](https://oldpapyrus.wordpress.com/tag/detect-ahci-enabled-bios-linux/)[/FONT]

I typed [COLOR=#2B2B2B][FONT=monospace][FONT=courier new]grep -inr ahci /proc/interrupts[/FONT] [FONT=arial]into a terminal and got a response:
   [FONT=courier new]11: 42:   1170    357    4274    952   PCI-MSI-edge    ahci

[FONT=arial]Hard to tell what this means though...?[/FONT][/FONT][/FONT][/FONT][/COLOR]

---

### Post by visctrix on 2014-06-25
Here's a better command [FONT=Ubuntu Mono]dmesg | grep -i ahci
[/FONT]Certainly seems that AHCI is enabled :)

---

### Post by oldfred on 2014-06-25
If you just used default install in BIOS boot for installer, it installs in MBR(msdos) unless empty drive and drive is somewhat over 1TB. gpt is required for drives over 2TiB.

I normally partition in advance with gparted to create gpt partition table, then use Something Else to choose /  partition and its format. My 2 yr old SSD has efi partition as I originally planned on moving SSD to a new system, but SSD made old system so much better I am only now planning new system again. And I have bios_grub so grub installs correctly in BIOS mode and two / (root) partitions, one 12.04 as current working and one 14.04 as soon to be working system.

Not sure which brand but some motherboard type issues.
 biostar A960D+ motherboard -MSI quirk detected
[http://ubuntuforums.org/showthread.php?t=2202279](http://ubuntuforums.org/showthread.php?t=2202279)
ubuntu 14.04 on asrock Z87 extreme 4 or pro 4 
[http://ubuntuforums.org/showthread.php?t=2216079](http://ubuntuforums.org/showthread.php?t=2216079)
Some have issues with Asrock and its asmedia ports
UEFI, Windows on SSD, Ubuntu on HD ASRock Z77 Pro4 motherboard
[http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/](http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/)
ASRock UEFI bios + Ubuntu Server = operating system not found  Install to flash drive
[http://ubuntuforums.org/showthread.php?t=2153123](http://ubuntuforums.org/showthread.php?t=2153123)
AsRock Z77 Windows always reset to default
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#Windows_changes_boot_order](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#Windows_changes_boot_order)

      
 Gigabyte GA-X79-UD3 with I7-3820
Needed F6 to set ACPI=Off.and nomodeset
Gigabyte UEFI boot issues - The partition size of the created USB Installer device needs to be under that of 4GB. 
Others found UEFI/BIOS update solved issue of 4GB FAT limit.
turns out the IOMMU needs to be enabled in the BIOS. This problems seems to be exclusive to Gigabyte boards.

---

### Post by visctrix on 2014-06-25
Ok. It's an MSI H87m E33 motherboard. Can't find any issues reported with that so far.

I'll try doing a secure erase of my SSD, partitioning it in advance with GParted, and start again... (tomorrow)

Thanks and good night :-)

---

### Post by oldfred on 2014-06-25
GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

      
 If using gpt with BIOS create a 1MB bios_grub partition with no format. I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....
My  first partition is an efi for future use, and bios_grub is required for booting with BIOS. If booting in BIOS mode using gpt create a 1 or 2MB bios_grub partition with no format.


```
Model: ATA SSD G2 series 64 (scsi)
Disk /dev/sde: 60.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name       Flags
 1      1049kB  316MB   315MB   fat32                   boot
 2      316MB   317MB   1049kB                          bios_grub
 3      317MB   30.2GB  29.9GB  ext4         Precise
 4      30.2GB  60.0GB  29.9GB  ext4         TrustySSD

```

---

### Post by visctrix on 2014-06-26
Tried that. No joy :-(

What next?

Some screenshots:
```
ubuntu@ubuntu:~$ sudo fdisk -lu

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   234441647   117220823+  ee  GPT

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001d0ec

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    97656831    48827392   83  Linux
/dev/sdb2        97658878   488394751   195367937    5  Extended
/dev/sdb5        97658880   107421695     4881408   82  Linux swap / Solaris
/dev/sdb6       107423744   224608255    58592256   83  Linux
/dev/sdb7       224610304   488394751   131892224   83  Linux
```

```
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA Samsung SSD 840 (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  41.9GB  41.9GB  ext4
 2      41.9GB  120GB   78.1GB  ext4


Model: ATA Hitachi HDT72102 (scsi)
Disk /dev/sdb: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  50.0GB  50.0GB  primary   ext4            boot
 2      50.0GB  250GB   200GB   extended
 5      50.0GB  55.0GB  4999MB  logical   linux-swap(v1)
 6      55.0GB  115GB   60.0GB  logical   ext4
 7      115GB   250GB   135GB   logical   ext4

```
```

ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/loop1: UUID="e9e9c786-4318-4571-8372-510099e2744e" TYPE="ext3" 
/dev/sda1: LABEL="/" UUID="991c8435-f4b9-422e-864c-252672843230" TYPE="ext4" 
/dev/sda2: LABEL="/home" UUID="fe39c286-8ee3-4c71-9c58-7440ba404d40" TYPE="ext4" 
/dev/sdb1: LABEL="root0" UUID="30e87429-7da9-4a40-b79a-83bdddeea2a1" TYPE="ext4" 
/dev/sdb5: UUID="d7a71cb9-cecf-4d51-aa94-cae128424dfd" TYPE="swap" 
/dev/sdb6: LABEL="home0" UUID="fbf11502-6c4d-45a9-9eda-e632131e11d2" TYPE="ext4" 
/dev/sdb7: LABEL="files0" UUID="7a31e65c-f375-447b-af33-6305af36ea18" TYPE="ext4" 
```

As far as I can tell after all the various checks the SSD is working ok.

I can see that it doesn't seem to be set as a boot drive. I guess I need to edit /etc/fstab. Can I do this with Gparted as gksu isn't on the liveUSB...? I'll try...

---

### Post by visctrix on 2014-06-26
Ok, thanks again oldfred!

I saw your last reply after I posted this morning. I've done that. Now the output of [FONT=courier new]sudo parted -l[/FONT] is:
```
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA Samsung SSD 840 (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  41.9GB  41.9GB  ext4
 2      41.9GB  41.9GB  1049kB                     bios_grub
 3      41.9GB  120GB   78.1GB  ext4


Model: ATA Hitachi HDT72102 (scsi)
Disk /dev/sdb: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  50.0GB  50.0GB  primary   ext4            boot
 2      50.0GB  250GB   200GB   extended
 5      50.0GB  55.0GB  4999MB  logical   linux-swap(v1)
 6      55.0GB  115GB   60.0GB  logical   ext4
 7      115GB   250GB   135GB   logical   ext4


```

Here's the content of /etc/fstab:
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=991c8435-f4b9-422e-864c-252672843230 /               ext4    acl,noatime,nodiratime,discard 1       1
# /home was on /dev/sda2 during installation
UUID=fe39c286-8ee3-4c71-9c58-7440ba404d40 /home           ext4    acl,noatime,nodiratime,discard 0       2
# swap was on /dev/sdb5 during installation
UUID=d7a71cb9-cecf-4d51-aa94-cae128424dfd none            swap    defaults             0       0
```

I've edited it in line with an article on SSD Tuning at [https://confluence.freeswitch.org/display/FREESWITCH/SSD+Tuning+for+Linux#SSDTuningforLinux-PrepareFSTABEntries ]("https://confluence.freeswitch.org/display/FREESWITCH/SSD+Tuning+for+Linux#SSDTuningforLinux-PrepareFSTABEntries")

My old /etc/fstab was:
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=991c8435-f4b9-422e-864c-252672843230 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda2 during installation
UUID=fe39c286-8ee3-4c71-9c58-7440ba404d40 /home           ext4    defaults        0       2
# swap was on /dev/sdb5 during installation
UUID=d7a71cb9-cecf-4d51-aa94-cae128424dfd none            swap    sw              0       0
```

I still get the error message that the disk with UUID=991c8435-f4b9-422e-864c-252672843230 doesn't exist...

Since making the edits with GParted I haven't reinstalled Ubuntu, so I don't know if the changes will make any difference...?

Cheers

Henry

---

### Post by visctrix on 2014-06-26
I've had a look at your link [http://askubuntu.com/questions/44696...y-vs-uefi-help]("http://askubuntu.com/questions/446968/legacy-vs-uefi-help") on the benefits of EFI.

Maybe I should try to follow that up and see if I can use this rather than avoid it...?

---

### Post by oldfred on 2014-06-26
I have only rarely seen the Alert! device does not exist before. But in the last few days there have been several. And no consistency with old or new or anything? Perhaps a new bug?

Usually it was older system with BIOS boot limit or system not in AHCI mode or system needed a new install of grub.

---

### Post by visctrix on 2014-06-29
Hi

My system is now working, phew! 
Some strange things happened in between, and I think the solution was simple and well documented in the end...?

The strange thing that happened was that I took out my new SSD that I couldn't boot from and put the old one back, but I got the same error - the disk with the UUID of the new SSD partition didn't exist! This was now true of course, but the old system shouldn't have known anything about that! How could it be looking for the UUID of the other SSD? Was it somehow recorded in the BIOS? I had already adjusted the BIOS by this point, and then I reset the BIOS to default setting and it still came back with the same error! (Then I ran boot-repair [which gave me an error message] and eventually it worked again.)

The solution (I tried so many things, but I think this was it) is detailed on [https://help.ubuntu.com/community/UEFI#Creating_an_EFI_partition](https://help.ubuntu.com/community/UEFI#Creating_an_EFI_partition). Then it worked :-)

Thanks oldfred, and sorry as it seems I led you on a (not so) merry dance...

---

