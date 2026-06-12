---
title: "Windows 7 not Detected during Ubuntu OS Installation"
date: 2015-03-31
forum: Installation &amp; Upgrades
---

### Post by rnvipin on 2015-03-31
Hello,

I've seen a quite few discussions on this, but I couldn't find suitable answers. So I had to open this thread. 

Motherboard : Gigabyte H61 MS, looks like UEFI enabled board.

I've assembled this and the vendor loaded a pirated Windows 7 OS. Back home, I removed it and installed an original Windows 7 Home Premium. Some messages popped up during the installation and I had to remove all the partitions and start from the scratch. So I'm not sure whether some UEFI firmware (I only came to know about such stuff after browsing on related discussions)

Next I went on to install Ubuntu and then came this famous message : "This computer currently has no detected operating systems". I've reserved a 25 GB partition for Linux, so I don't have to shrink partition as suggested in many discussions. 

I don't want to be in trouble after installing Ubuntu to make the system inoperable. Please help me with this.

Thanks,
Vipin

---

### Post by oldfred on 2015-03-31
If original install was UEFI with gpt partitions and you reinstalled with BIOS and MBR partitions, Windows converted from gpt to MBR incorrectly. 

Post this:
sudo fdisk -lu
sudo parted -l

If it shows MBR with gpt signatures  you can use fixparts to remove left over gpt data. Or reinstall Windows in UEFI boot mode. You may have to make a couple of minor modifications to Windows 7 installer to be a UEFI installer.

       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by rnvipin on 2015-04-01
Hello,

Thank you for responding. Here is the information you've asked for :-

ubuntu@ubuntu:~$ sudo fdisk -lu

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xf84c1ad0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  1953525167   976762583+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdb: 16.0 GB, 16013852672 bytes
255 heads, 63 sectors/track, 1946 cylinders, total 31277056 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    31277055    15637504    7  HPFS/NTFS/exFAT
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA WDC WD10EZRX-00L (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system     Name                          Flags
 1      1049kB  106MB   105MB   fat32           EFI system partition          boot
 2      106MB   240MB   134MB                   Microsoft reserved partition  msftres
 3      240MB   210GB   210GB   ntfs            Basic data partition          msftdata
 4      210GB   420GB   210GB   ntfs            Basic data partition          msftdata
 5      420GB   445GB   25.2GB  ext4            Basic data partition          msftdata  (Ext4)
 8      445GB   446GB   900MB   linux-swap(v1)                                                  (Swap) 
 9      446GB   446GB   101MB                                                 bios_grub           (Reserved BIOS Area chose in time of Ubuntu install)
 6      446GB   656GB   210GB   ntfs            Basic data partition          msftdata
 7      656GB   1000GB  345GB   ntfs            Basic data partition          msftdata

I went on and installed Ubuntu. Now Grub is not shown at all.

Thanks,
Vipin

---

### Post by oldfred on 2015-04-01
It looks like you originally did install Windows 7 in UEFI mode, but with the bios_grub partition that would be a BIOS/CSM boot of Ubuntu.
UEFI and BIOS are not compatible. You cannot change boot once started, or cannot dual boot from grub menu. But you should be able to boot from UEFI boot menu. But may have to change UEFI settings to match install or turn on/off UEFI or CSM/BIOS mode.

If you had a secure boot setting (I did not think early motherboards with UEFI did) then that may have been on, or you were trying to boot in wrong mode, so nothing seen.

May  be best to see details, post link to summary report:
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by rnvipin on 2015-04-02
Hello,

The whole scenario is still opaque for me, however I found the following : 

UEFI Booting leads to Windows 7 (No Grub shown)
SATA Mode Booting leads to Ubuntu (No Grub shown)

I guess leaving 100 MB for BIOS Reserved while installing Ubuntu made this complicated. Maybe I should re-install Ubuntu without BIOS Reserved space ?

Thanks,
Vipin

---

### Post by rnvipin on 2015-04-02
Please find the Boot info summary here :-

[http://paste.ubuntu.com/10722218/](http://paste.ubuntu.com/10722218/)

Let me ask, is the current setup safe for the system ? I've no issues (without grub) and in booting from Boot Menu whenever I need Linux.

---

### Post by oldfred on 2015-04-02
If willing to dual boot only from UEFI boot menu or perhaps one time boot key like f10 or f12 then your install is ok.
But a bios_grub partition only needs to be 1 or 2MB. It is just for part of grub (core.img) that with MBR partitioning would be in the sectors after the MBR has a place as with gpt there is no unavailable  space after gpt's protective MBR.  

I also like that you labelled your partitions, but with Linux often better not to use spaces. I use CamelCase, under_score, or justaname. With the space if using command line you have to either add quotes or escape the space which can be confusing.

---

