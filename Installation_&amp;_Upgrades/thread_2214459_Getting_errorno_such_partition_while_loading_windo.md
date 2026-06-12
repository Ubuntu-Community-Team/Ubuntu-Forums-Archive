---
title: "Getting error:no such partition while loading windows 8 after ubuntu 12.04 installati"
date: 2014-04-01
forum: Installation &amp; Upgrades
---

### Post by shashank.ks on 2014-04-01
[ATTACH=CONFIG]251642[/ATTACH][ATTACH=CONFIG]251642[/ATTACH][ATTACH=CONFIG]251642[/ATTACH]Hi,

       I had shrinked volume on windows 8 to create a partition and installed ubuntu 12.04 after creating boot and home partition. But now on selecting windows from the boot menu i am getting "error: no such partition" error. i can boot in to ubuntu. I have backed up windows 8. i tried restoring windows 8 and again installing the ubuntu 12.04. Still seeing the same error. I tried using the boot-repair after booting in to ubuntu with usb. The boot-repair gave a like "http://paste.ubuntu.com/7189943". i see only one partition with "sudo fdisk -l" output. But i see all the partition with the gparted software. I have attached screenshot of gparted. 


$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x7d9b2a38

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  1953525167   976762583+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdb: 8004 MB, 8004304896 bytes
35 heads, 21 sectors/track, 21269 cylinders, total 15633408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000df82d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32    15633407     7816688    b  W95 FAT32
$

---

### Post by oldfred on 2014-04-01
Do not use fdisk on gpt partitioned drives. Use parted or download and use gdisk which is the fdisk for gpt partitioned drives.

Grub used to have a bug and only created BIOS boot entries even when Ubuntu & Windows were UEFI. The entry has to chain load to the efi partition, not like a BIOS entry to the Windows partition.
It also has a bug where it will not boot 8.1 if secure boot is on.

 Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
If you run any fixes from Boot-Repair do not say yes to 'buggy' UEFI. That is only for systems where UEFI has been modified by vendor to only allow Windows to boot.


 Unable to chainload Windows 8 with Secure Boot enabled  Also post #11 on using refind
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091464](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091464)
      
 grub-update fails to detect windows bootloader on a uefi system
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801)
grub2's os-prober creates wrong style (BIOS) chain boot entry Fixed with 13.10
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)

---

