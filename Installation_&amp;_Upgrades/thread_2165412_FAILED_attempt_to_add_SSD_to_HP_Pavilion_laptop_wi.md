---
title: "FAILED attempt to add SSD to HP Pavilion laptop with HDD dual booting Ubuntu + Win8"
date: 2013-08-04
forum: Installation &amp; Upgrades
---

### Post by Dr_Michael_Brooks on 2013-08-04
Hi,

I've broken both my Windows 8 and Ubuntu booting on my laptop with the help from boot-repair. Can you help me get my laptop booting Ubuntu off its new SSD?

I have an HP Pavilion Laptop which contains a 1TB magnetic drive natively. It was booting Ubuntu 12.10 and Windows 8 happily via a Grub EFI on that drive. My intention was to move the Ubuntu 12.10 partition to the SSD and boot from that as the primary device and use fstab to mount the magnetic HDD as bulk storage. I did a fresh backup of all important files and configs to my network drive prior to dicking about.

I removed the laptop's CD/DVD optical drive and fitted it with an opti-bay caddy and a Samsung 250GB SSD. I partitioned the SSD to have: 800MB FAT32, 12GB swap, the remainder for ext4 /;  I used Clonezilla to copy the partition containing Ubuntu 12.10 to the SSD's ext4 formatted partition.

My next step was to make the SSD bootable so I could tell the BIOS to boot from that as first choice. I put in a Live USB of Ubuntu 13.04 and booted into it (had to use the boot menu to navigate manually to the stick's EFI file to get round HP's annoying firmware bug where booting from a USB causes a hang). I installed boot-repair and followed the instructions on the Ubuntu Boot-Repair page ([https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)) with the UEFI advice in mind ([https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)). It detected my EFI partition, I went to >advanced options and selected the appropriate partition to install the EFI bootloader. All apparently ran well.

I restarted my laptop and went into the BIOS, changing the boot order to boot from the "CD/DVD drive" (i.e. the SSD) first, before the magnetic HDD. I saved this, exited and booted. However, the SSD didn't offer any bootloader at all, and the system reverted to booting from the HDD and produced a Windows 8 error screen stating that "Your system needs repairing".

The output of Boot-repair is here: [http://paste.ubuntu.com/5949455/](http://paste.ubuntu.com/5949455/)
(sda = magnetic hard drive, sdb = new SSD)

Now I'm not bothered about Windows 8*, but I absolutely need to be able to boot into Ubuntu, preferably on the SSD and preferably with all my packages installed and configured how I like them. I have tried all sorts of partitioning, re-partitioning, re-copying, re-Clonezillaing, re-boot-repairing of sdb with no success. How can I make my SSD boot my Ubuntu image?

Cheers,
Mike

[SIZE=1](* Windows 8 is a Janus-faced cluster**** of an OS. It's dreadful)[/SIZE]

---

### Post by oldfred on 2013-08-05
Does your system boot from the SSD in the DVD position? Some (not sure what computer) have said that the drive in a CD/DVD caddy is not bootable, but is just a data drive.

The efi partition per UEFI spec is supposed to be first, most Windows systems seem to have it second or third but only smaller partitions in front of it so it is still near front of drive. Not sure how far into a drive UEFI's driver can read the boot partition as it is somewhat limited.

It looks like you have grub installed to the MBR of the SSD, which is a BIOS/CSM boot not UEFI. And to dual boot both Windows and Ubuntu have to be either UEFI or both BIOS. And Windows only boots from gpt drives with UEFI, so both installs need to be UEFI.

You also removed efi and Windows system reserved partitions from sda. Windows needs those partitions on sda to boot. It looks like sda2 is really your efi partition, but that is defined by the boot flag. You may have removed boot flag and converted it back to a data partition. And sda3 was probably the Windows system reserved. Unformat it with gparted and add the System Reserved flag or partition type with gparted.

Windows has this suggestion:
 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

And this is my suggestion for Ubuntu and if gpt partitioned, have an efi partition at the beginning (or near it) on every drive.

      
 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 250 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

Wubi does not work with gpt partitioned drives or therefore any system with Windows 8. So remove wubi from your Windows 8 partition. 

If you can dual boot from SSD in caddy, see my signature for links to several users with dual UEFI installs. But I think they all were desktops with two standard drives or SSD & hard drive.

---

