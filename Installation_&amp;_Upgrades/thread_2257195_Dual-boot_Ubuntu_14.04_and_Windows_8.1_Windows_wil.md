---
title: "Dual-boot Ubuntu 14.04 and Windows 8.1: Windows will not boot"
date: 2014-12-17
forum: Installation &amp; Upgrades
---

### Post by Hans83VT on 2014-12-17
I know there are a lot of threads about getting Ubuntu and Windows to work together, but I haven't found any that seem specific to my situation.

The system has one SSD with a classic MBR table (not GPT).  UEFI and Secure Boot are both disabled in the BIOS.

I installed Windows 8.1 first on approximately half of the SSD - it boots just fine.  I disabled fast boot in Windows and then installed Ubuntu 14.04.1 from CD - it sees the Windows partition and offers to install alongside Windows, which I select.  Once installed, Ubuntu boots just fine, but when I select Windows from the boot manager, it just goes to a purple screen and sits there.

I wiped the machine and tried again - the same problem occurs.   I also tried installing Boot Repair.  The results are here: [http://paste.ubuntu.com/9555356/](http://paste.ubuntu.com/9555356/)

Any ideas? Thanks in advance for your help.

---

### Post by oldfred on 2014-12-17
Boot-Repair says you left fast boot on.

>  The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda1': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
mount -t ntfs-3g -o remove_hiberfile /dev/sda1 /mnt/boot-sav/sda1




And grub cannot boot Windows with fast boot on. And grub only boots working Windows, so best to have a Windows repair CD or flash drive.

You may temporarily install a Windows boot loader to the MBR and boot Windows. Be sure to turn off fast boot and then restore grub to MBR. Advanced mode in Boot-Repair lets you choose operating system and drive to install boot loader into, so you can use that for both fixes. But Boot-Repair cannot fix most Windows issues.

       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

    
 Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

UEFI has the advantage of each system has its boot files in the efi partition as separate folders. So it is somewhat like having multiple MBR with different boot loaders all on one drive. And from UEFI you can then boot any system without having to reinstall boot loaders. But UEFI as implemented by Windows and secure boot create lots of other issues.

---

### Post by Gordonbp531 on 2014-12-18
Create the free space for your Ubuntu install within Windows using Disk management.
Allowing the Ubuntu installer to do so has some strange effects on a pre-existing Windows 8 install, one of which is that it won't boot.
Then boot from the lice CD/USB and choose "something else" in the install dialog box instead of allowing Ubuntu to automatically install along side.

the other reason for Windows not booting is that you've disabled UEFI. Windows 8.x won't boot (AFAIAA) unless it's installed in UEFI mode, and UEFI is enabled.
Why are yoiu using 12.04? 14.04 has been out for 9 months nearly, and it will install perfectly well on UEFI, whereas 12.04 support for UEFI was a bit flakey...

---

