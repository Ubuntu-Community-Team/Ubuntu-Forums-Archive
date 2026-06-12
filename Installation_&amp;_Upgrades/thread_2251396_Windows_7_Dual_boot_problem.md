---
title: "Windows 7 Dual boot problem"
date: 2014-11-04
forum: Installation &amp; Upgrades
---

### Post by markus19 on 2014-11-04
Hi,

Just bought a new computer that came with Windows 7 pre-installed. The machine has an SSD and a HD. I intend to use SSD for programs, HD for data. I managed to shrink the Windows 7 partition as explained in the tutorials, disabled secure boot in bios, enabled booting from CD and then went on to install Ubuntu.

Here's my partition layout:
[ATTACH=CONFIG]257735[/ATTACH]
[http://imgur.com/uoq3i8e](http://imgur.com/uoq3i8e)

Disk0 (/dev/sda) is the SSD that I want to install Ubuntu on. 

When installing Ubuntu the installer does *not* offer the option to install alongside Windows 7 as I've seen in some tutorials / videos. I'm only given the option to wipe the disk or "something else". With "something else" I end up in the partitioning tool and can setup where to install etc. It also asks were to install the boot-loader, but doesn't offer dual-boot options.

I tried installing with selecting /dev/sda for the boot-loader. This installed Ubuntu (14.10) into the partition I wanted, but I wasn't able to boot Windows 7 anymore (no grub or windows boot-loader came up; it went straight into Ubuntu). I restored the disk from a backup and tried the 14.04.1 version of Ubuntu as I had seen this version in a video. Again, it didn't offer a dual install option (only wipe or "something else"). Trying to setup things in the partition tool looked the same. I tried selecting the first small partition as EFI partition, but the installation aborted early on saying it couldn't mount the partition with vfat (it looks like it's ntfs).

Any advice on how to get Ubuntu and Windows7 to co-exist? Any additional information I should post?

Thank you.

---

### Post by yancek on 2014-11-04
With the number of healthy primary partitions showing from your windows output, it appears you are using GPT/UEFI for windows 7.  Is that the case?  If so, you need to install Ubuntu in GPT/UEFI also.

---

### Post by oldfred on 2014-11-04
Windows usually shows an efi partition. And Windows in BIOS/MBR mode has a 100MB hidden boot partition which it looks like you have. 
Better to see partition details from Linux, so we can tell for sure.

Post this:
sudo fdisk -lu
sudo parted -l

Since you may have BIOS boot for Windows you should then install Ubuntu in BIOS boot mode. But either way both systems should be in same boot mode. 
Windows 7 does not use secure boot and does not have the always on hibernation or fast boot. But best not to turn on hibernation if dual booting.

---

### Post by markus19 on 2014-11-04
Thank you for helping. Here's the output:

> ubuntu@ubuntu:~$ sudo fdisk -lu /dev/sda

Disk /dev/sda: 240.1 GB, 240057409536 bytes
255 heads, 63 sectors/track, 29185 cylinders, total 468862128 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x36bd27b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   283588607   141690880    7  HPFS/NTFS/exFAT
/dev/sda3       283588608   308754431    12582912    6  FAT16
/dev/sda4       308756478   468858879    80051201    f  W95 Ext'd (LBA)
/dev/sda5       308756480   468858879    80051200   83  Linux

ubuntu@ubuntu:~$ sudo parted -l
Model: ATA INTEL SSDSC2BP24 (scsi)
Disk /dev/sda: 240GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system  Flags
 1      1049kB  106MB  105MB   primary   ntfs         boot
 2      106MB   145GB  145GB   primary   ntfs
 3      145GB   158GB  12.9GB  primary
 4      158GB   240GB  82.0GB  extended               lba
 5      158GB   240GB  82.0GB  logical   ext4


Model: ATA WDC WD10EZEX-07M (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  430GB   430GB   primary   ntfs
 2      430GB   1000GB  570GB   extended
 5      430GB   496GB   65.5GB  logical   ext4
 6      496GB   561GB   65.5GB  logical   linux-swap(v1)
 7      561GB   1000GB  439GB   logical   ext4


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!                           


How does one install Ubuntu in BIOS mode or with GPT/UEFI? I didn't see any options during installation.

---

### Post by yancek on 2014-11-04
Ignore my post above regarding GPT as I misread your image.  The main window shows all the partitions on both drives without identifying them except below.

If you are able to boot Ubuntu, open a terminal and enter the command:  sudo update-grub (you should be prompted for your primary user password, enter that and hit the Enter key)
Watch the output for a windows entry.  You have a  Linux partition on sda5 (240GB drive) and you also have Linux partitions on the 1TB drive, partitions 5 and 7.  Are those data partitions for Ubuntu?  You can verify that you are booting the SSD when you boot Ubuntu, open a terminal and type the following command:  df -h

You should see output similar to that below, look for the partition under the Filesystem column showing /dev/sda5 and it should show / under mounted on which means that is your Ubuntu root filesystem partition.  If it shows /dev/sdb5 or 7, then it is on the other drive.

> df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda5        39G   27G   10G  73% /


---

### Post by oldfred on 2014-11-04
UEFI & BIOS are not compatible.
 CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 


And the only time you get a choice between them is when you boot from UEFI menu. 
If a flash drive you should have two entries one UEFI and one not or usually just the label of flash drive.

Once installed again the only time you get a choice is from UEFI/BIOS menu. And usually you have to turn on/off UEFI or on/off CSM boot mode. 
Best just to set default boot mode in UEFI/BIOS and install all systems in that one boot mode.

---

### Post by markus19 on 2014-11-05
Yancek, I restored my disk from backup, but Ubuntu was installed on /dev/sda5. Currently I can only boot windows7 and the partition you see marked as linux is formated but with nothing on it. So should I try to install ubuntu as I had before, but try to run "[COLOR=#000000]sudo update-grub" to get windows7 to re-appear in the bootloader?[/COLOR]

oldfred, I'm a bit confused from your response. What would the UEFI menu look like or where would I find that? I didn't see anything that look like a boot menu (grub/windows). And would you advice I should try?

---

### Post by yancek on 2014-11-05
The partition information you posted earlier seems to indicate you are using MBR rather than UEFI for your system.  Do you have a UEFI option in your BIOS?  I think the best way to get more detailed information is to get the boot repair script from the link below.  Select the option to Create a Boot Info Summary and then post the link here.

[http://sourceforge.net/p/boot-repair-cd/home/Home/](http://sourceforge.net/p/boot-repair-cd/home/Home/)

---

### Post by oldfred on 2014-11-05
UEFI is the replacement for BIOS. All new computers with Windows 8 pre-installed have UEFI (and secure boot). A few computers before Windows 8 came out had UEFI hardware but Windows 7 usually was still in CSM/BIOS boot mode.

But when you got into UEFI/BIOS and have UEFI, you get options to turn on/off UEFI or turn on/off CSM. Since you are BIOS you want to make sure you only use BIOS boot mode if you have the option. 
Typically flash drives will show two boot options from UEFI menu.

This shows the two entries for a Toshiba flash drive. One says Toshiba and the other says UEFI Toshiba.

---

### Post by markus19 on 2014-11-06
ok, so in my bios I found a CSM mode setting. It's set to:
> 
launch csm: enabled
boost device control: uefi and legacy oprom
boot from network: legacy only
boot from storage devices: legacy only
boot from pci-e/pci expansion devices: legacy only

The boost/secure-boot is set to: "other os"

If I understand that correctly then I should still boot from disk using legacy MBRs etc. That would mean I shouldn't see an UEFI menu, correct?

Boot-repair disk at [http://pastebin.com/B6R9XF2R](http://pastebin.com/B6R9XF2R) (file too large to attach).

---

### Post by oldfred on 2014-11-06
You should still have a boot menu in the UEFI/BIOS. But now you should only be booting with CSM/BIOS mode.

My Asus motherboard had similar settings and I could only get it to boot in UEFI mode by changing to other OS, and going into CSM and from CSM turn on UEFI. And even UEFI or CSM setting would not offer to boot flash drive in UEFI mode. Only the UEFI only mode setting would boot in UEFI. 
Or while UEFI is a standard how it is implemented varies a lot by vendor.

---

### Post by markus19 on 2014-11-07
Success!

I enabled CSM mode in my bios and reinstalled Ubuntu. As before windows7 wasn't shown during the installation. Upon rebooting after the installation there was no boot menu and no way to boot windows7. I booted Ubuntu, run "sudo os-prober" which found windows7, and then run "sudo update-grub". Upon rebooting grub showed up showing both Ubuntu and Windows7 as an option. Both OS can be booted now.

Thank you both so much for your help!

---

