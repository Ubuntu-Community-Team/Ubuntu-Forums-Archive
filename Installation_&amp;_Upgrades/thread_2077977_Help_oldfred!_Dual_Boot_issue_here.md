---
title: "Help oldfred! Dual Boot issue here"
date: 2012-10-29
forum: Installation &amp; Upgrades
---

### Post by burpootus on 2012-10-29
I have a UEFI/GPT computer with 3 drives, sda for linux Xubuntu 12.04 (EFI partition on sda1), sdb formatted ext4 for data, and sdc formatted NTFS for data. I added a 4th drive, sdd and installed Win 8 (sda unplugged during the install). The Win 8 install created an EFI partition on sdd1. So I plug sda back up and set it as the boot drive, boot into linux and run boot-repair. But when I reboot into grub, it won't boot windows. The grub entry looks wrong to my untrained eye:

menuentry "Windows 8 (loader) (on /dev/sdd1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd3,msdos1)'
	search --no-floppy --fs-uuid --set=root D8C2389FC2388432
	drivemap -s (hd0) ${root}
	chainloader +1 

And here is the full report from boot-repair:

[http://paste.ubuntu.com/1316737/](http://paste.ubuntu.com/1316737/)

How do I get grub to load the correct EFI boot windows file(s)?

Thanks much!


EDIT: 2012-11-2 Followed suggestions in thread, used Gparted to delete the EFI partition sda1 and make it a bios-grub boot partition. Ran boot-repair and now Xubuntu 64 bit and Win 8 Pro 32 bit both boot from the grub menu as expected.

---

### Post by oldfred on 2012-10-29
It does not help to put me in the title. 

Actually you will do better with Boot-Repair.

The grub2 os-prober makes a BIOS type chain loader entry. But Yann has updated Boot-Repair to add correct chain entries to the Windows file in the efi folder. He was adding three entries to all the Windows files & 2 worked as posted by several users. 

UEFI dual boot two drives See page 3 on the first thread for typical boot stanza. 
[http://ubuntuforums.org/showthread.php?t=2072950](http://ubuntuforums.org/showthread.php?t=2072950)
[http://ubuntuforums.org/showthread.php?t=2031836](http://ubuntuforums.org/showthread.php?t=2031836)
UEFI dual boot trouble: Win7x64 - Ubuntu 12.04 LTS amd64
[http://ubuntuforums.org/showthread.php?t=2003442](http://ubuntuforums.org/showthread.php?t=2003442)
UEFI screen shots with choice to boot
[http://ubuntuforums.org/showthread.php?p=12030957#post12030957](http://ubuntuforums.org/showthread.php?p=12030957#post12030957)


dual boot efi windows and efi linux 
[http://ubuntuforums.org/showthread.php?t=1890048](http://ubuntuforums.org/showthread.php?t=1890048)

---

### Post by burpootus on 2012-10-30
Thanks for the links. Unfortunately I'm still stuck with having to go into the BIOS and selecting the Linux or Win 8 drive to dual boot. I've tried every form of syntax I can find to make a suitable grub menu entry and none of them will boot Win 8. Win 8 is somewhat different than Win 7. The EFI partition it makes during the install seems to be NTFS instead of FAT. I was under the impression that FAT was the EFI partition standard. The path and boot file are different as well. Everything I've seen about Win 7 indicates a boot file path like /EFI/Microsoft/Boot/bootmgfw.efi. In Win 8, there is no .efi file in the System Reserved (sdd1, "EFI") partition. It appears that the file bootmgr (no extension) in the root of System Reserved is the boot file.

---

### Post by oldfred on 2012-10-30
Is it in BIOS mode which has a small 100 or now 200MB hidden NTFS boot/repair partition which is usually first or second after a recovery partition or an efi partition which has efi boot files?

Post the link to the BootInfo report that this creates.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by burpootus on 2012-10-31
The boot info link is in the OP. I hadn't really thought about Win 8 installing itself in BIOS mode. I assumed that since this MOBO (Asus P8Z68-V LX) is UEFI and I did a clean install (Win 8 installer formatted and automatically setup partitions 1 & 2 on /dev/sdd) that Win 8 boots in UEFI mode. This is my first build using UEFI, so I'm learning as I go. I didn't know it was possible to mix and match UEFI and BIOS/MBR in the same PC.

---

### Post by darkod on 2012-10-31
I haven't used uefi nor win8. But looking at your bootinfo it seems to me quite clear that win8 instaled in bios (legacy) mode and not in uefi.

I think both windows and ubuntu don't look at whether your board is uefi or not. They don't care. It seems you need to control the mode in which the OS will install by selecting the correct boot device.

For example, on uefi enabled boards there will be two devices for your dvd drive. There will be the legacy bios device, and uefi dvd drive. [COLOR="Red"]You need to boot the cd/dvd/usb stick in uefi mode so that the OS installs in uefi mode.[/COLOR] The same is true when repairing windows for example. It has been noticed that if you boot the repair/install media in legacy mode, it will not see the existing uefi installation of windows because it's not booted in uefi mode.

See if that helps. You might need to redo the win8 install making sure the media boots in uefi mode.

PS. There is usually a setting in bios that controls whether you can mix them. The options usually are Legacy Only, UEFI Only, and Both. So, depending what you select it will allow you to mix, or limit you only to one type of boot.

---

### Post by YannBuntu on 2012-10-31
> **burpootus said:**
> here is the full report from boot-repair:

[http://paste.ubuntu.com/1316737/](http://paste.ubuntu.com/1316737/)

How do I get grub to load the correct EFI boot windows file(s)?

Hello

Your Windows is installed in Legacy mode only. (@fred& darkod: .efi.grb files indicate that the corresponding .efi is fake)
So you need to:
1) via Gparted, erase sda1 and make it a BIOS-Boot partition. [https://help.ubuntu.com/community/DiskSpace#BIOS-Boot_or_EFI_partition_.28required_on_GPT_disks.29](https://help.ubuntu.com/community/DiskSpace#BIOS-Boot_or_EFI_partition_.28required_on_GPT_disks.29)
2) then convert your Ubuntu into Legacy mode too. [https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_Legacy_mode](https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_Legacy_mode) (indicate us the new URL that will appear)
3) make your BIOS boot your hard-disk in Legacy mode  (= disable UEFI)

---

### Post by darkod on 2012-10-31
> **YannBuntu said:**
> Hello

Your Windows is installed in Legacy mode only. (@fred& darkod: .efi.grb files indicate that the corresponding .efi is fake)
So you need to:
1) via Gparted, erase sda1 and make it a BIOS-Boot partition. [https://help.ubuntu.com/community/DiskSpace#BIOS-Boot_or_EFI_partition_.28required_on_GPT_disks.29](https://help.ubuntu.com/community/DiskSpace#BIOS-Boot_or_EFI_partition_.28required_on_GPT_disks.29)
2) then convert your Ubuntu into Legacy mode too. [https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_Legacy_mode](https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_Legacy_mode) (indicate us the new URL that will appear)
3) make your BIOS boot your hard-disk in Legacy mode  (= disable UEFI)

That's what I said, win8 is installed in legacy.

The OP can do the other way around, since he installed win8 last and it seems he wants UEFI setup. He can delete this win8 install and do a new one making sure it's installed in uefi mode. That should work, right?

---

### Post by burpootus on 2012-10-31
Thanks for the replies. I typically build a rig every 3 years. When I built this one last July I purposely set it up to be UEFI. No real reason other than it seemed like a good time, and I'd read some things about Win 8 requiring UEFI. I built the rig to be Linux only, with the possibility of dual booting in the future. So when the $39.99 Win 8 Pro upgrade offer became available, I thought I'd give it a shot. So I'm not too proud to revert Linux back to BIOS /MBR mode since that is a known painless path. It appears that the other option is to re-install Win 8 in EFI mode. I wish the option existed to convert the Win 8 System Reserved partition to GPT and turn Win 8 into an EFI boot OS, much the same way Linux can be reverted backwards.

---

### Post by oldfred on 2012-10-31
Perhaps it got confused, your sda1 FAT32 shows this, then not finding a efi partition it did not install correctly:

>     Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 2048.Windows NTFS and then I assume FAT32 have to have the same info in the PBR - partition boot sector as the partition table. Usually chkdsk fixes it. So I might run chkdsk on your sda1 partition.

Windows 8 UEFI repair USB must be FAT32
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)

Do not know if you can convert 8 the same as 7 or not?

Windows Recommended UEFI-Based Disk-Partition Configurations
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx]("http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx")
Change the booting style of Windows Vista or 7 x86_64 versions from BIOS-MBR mode to UEFI-GPT mode without formatting or reinstalling
[https://gitorious.org/tianocore_uefi_duet_builds/pages/Windows_x64_BIOS_to_UEFI](https://gitorious.org/tianocore_uefi_duet_builds/pages/Windows_x64_BIOS_to_UEFI)
Windows installs the efi bootloader to (ESP)/EFI/Microsoft/Boot/ which is identical to (WINDOWS_SYSTEM_PART)/boot/microsoft/ incase of BIOS systems.

---

### Post by burpootus on 2012-10-31
> **oldfred said:**
> Perhaps it got confused, your sda1 FAT32 shows this, then not finding a efi partition it did not install correctly:

Windows NTFS and then I assume FAT32 have to have the same info in the PBR - partition boot sector as the partition table. Usually chkdsk fixes it. So I might run chkdsk on your sda1 partition.

Windows 8 UEFI repair USB must be FAT32
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)

Do not know if you can convert 8 the same as 7 or not?

Windows Recommended UEFI-Based Disk-Partition Configurations
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx]("http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx")
Change the booting style of Windows Vista or 7 x86_64 versions from BIOS-MBR mode to UEFI-GPT mode without formatting or reinstalling
[https://gitorious.org/tianocore_uefi_duet_builds/pages/Windows_x64_BIOS_to_UEFI](https://gitorious.org/tianocore_uefi_duet_builds/pages/Windows_x64_BIOS_to_UEFI)
Windows installs the efi bootloader to (ESP)/EFI/Microsoft/Boot/ which is identical to (WINDOWS_SYSTEM_PART)/boot/microsoft/ incase of BIOS systems.

I had sda unplugged during the Win 8 install. I did notice sda1 starting on 2048 in the report and wondered where the first megabyte or so of the drive disappeared to. Reading the Tianocore link you posted, it says that Win 7 32 bit does not support UEFI booting. There's no updated info for Win 8, but unfortunately (my rig has 16 gigs of RAM) my version is 32 bit. I wonder if that's my issue? I didn't boot the Win 8 upgrade DVD any different than I booted the Xubuntu DVD back when I first installed. I had to direct the Xubuntu installer to create an EFI partition, etc., so it installed in UEFI mode. I did a clean install of Win 8 where it started with sdd as unallocated space. I had no options at that point, it was all automatic. Probably my best option at this point is to convert Xubuntu over to legacy and be done with it.

---

### Post by oldfred on 2012-10-31
If you have all that RAM you definitely want 64 bit for everything.

Linus does not like PAE or 32 bit.
[http://cl4ssic4l.wordpress.com/2011/05/24/linus-torvalds-about-pae/](http://cl4ssic4l.wordpress.com/2011/05/24/linus-torvalds-about-pae/)

[http://ubuntuforums.org/showthread.php?t=2028717](http://ubuntuforums.org/showthread.php?t=2028717)
Ubuntu 12.10: 32-bit vs. 64-bit Linux Performance
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_1210_3264&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1210_3264&num=1)
Assuming your hardware is x86_64 capable (basically any modern Intel/AMD CPU) and have at least 2GB of RAM, you really should be running the 64-bit version.
Essentially says if you can use the 64bit kernel you should.April 2011
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1)

Vista was the first to convert to starting at sector 2048. Linux changed later, but all default installs now start at sector 2048.

Since drives became over 8GB CHS cylinders, heads, sectors has been obsolete and LBA is how drive is configured. For more compatibility with newer drives, 4k drives, SSDs and better configuration, partitions now start at sector 2048 rather than rounding to cylinders. With 512 bytes per sector that is 1MB at the beginning of the drive.
[http://en.wikipedia.org/wiki/Cylinder-head-sector](http://en.wikipedia.org/wiki/Cylinder-head-sector)

First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)

---

### Post by burpootus on 2012-10-31
> **oldfred said:**
> If you have all that RAM you definitely want 64 bit for everything.

Linus does not like PAE or 32 bit.
[http://cl4ssic4l.wordpress.com/2011/05/24/linus-torvalds-about-pae/](http://cl4ssic4l.wordpress.com/2011/05/24/linus-torvalds-about-pae/)

[http://ubuntuforums.org/showthread.php?t=2028717](http://ubuntuforums.org/showthread.php?t=2028717)
Ubuntu 12.10: 32-bit vs. 64-bit Linux Performance
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_1210_3264&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1210_3264&num=1)
Assuming your hardware is x86_64 capable (basically any modern Intel/AMD CPU) and have at least 2GB of RAM, you really should be running the 64-bit version.
Essentially says if you can use the 64bit kernel you should.April 2011
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1)

Vista was the first to convert to starting at sector 2048. Linux changed later, but all default installs now start at sector 2048.

Since drives became over 8GB CHS cylinders, heads, sectors has been obsolete and LBA is how drive is configured. For more compatibility with newer drives, 4k drives, SSDs and better configuration, partitions now start at sector 2048 rather than rounding to cylinders. With 512 bytes per sector that is 1MB at the beginning of the drive.
[http://en.wikipedia.org/wiki/Cylinder-head-sector](http://en.wikipedia.org/wiki/Cylinder-head-sector)

First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)

Yep, my Xubuntu is 64 bit. I don't think it has ever used the swap partition, even when also running a Win 7 VM. I don't have a 64 bit version of Windows, so unfortunately I can't download a 64 bit Win 8 upgrade for $39.99.

I'll mark this thread as SOLVED when I successfully revert Xubuntu to legacy boot. Thanks for everyone's help.

---

