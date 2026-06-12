---
title: "Not BOOT and Grub 2 screen after installing ubuntu 18.04"
date: 2018-10-07
forum: Installation &amp; Upgrades
---

### Post by alex55555 on 2018-10-07
I install Ubuntu from DVD writen from iso, which i download from official site today. After install i reboot and see Grab screen. I found solution for booting on forum and when i enter this:
```
set prefix=(hd1,10)/boot/grub
set root=(hd1,10)
insmod ext2
insmod normal
normal
```
I boot and system was loaded. Then i run boot repair utility and choose recommended method, but after reboot Grab screen appears again. Attachments not works, then here link to report from repair program: [http://paste.ubuntu.com/p/rnwR3ZWH6P/](http://paste.ubuntu.com/p/rnwR3ZWH6P/)

---

### Post by oldfred on 2018-10-07
You have mixed UEFI Secure Boot, UEFI boot, &  BIOS boot.
So you must have newer hardware that is UEFI which has the option to turn on Secure Boot. But also has a mode to allow booting an old system using CSM.
        CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

You have Windows installs & drive is MBR(msdos). Windows then only boots in BIOS mode from MBR partitioned drives.
Windows also only boots in UEFI mode from gpt, but install is so different, that it is difficult or impossible to convert, you have to reinstall if you want UEFI.

But Ubuntu is not as particular. It will install in UEFI or BIOS mode to gpt partitioned drives. Or  in UEFI boot mode from MBR partitioned drives.
UEFI strongly suggests using gpt with UEFI.

You have installed Ubuntu in UEFI mode & Windows in BIOS boot mode.
You also have both grub in BIOS boot mode in the MBR, but an ESP - efi system partition for UEFI boot.

You probably are not booting with correct grub, but it lets you manually boot. Only real differnce between UEFI & BIOS installs of grub is grub version, grub-pc for BIOS and grub-efi-amd64 for UEFI.

You can use Boot-Repair to convert your install to BIOS boot, since drive is MBR. 
But you must turn off UEFI Secure Boot in UEFI settings. You may also have to turn on allow USB boot.  
Then boot in BIOS mode, and in Boot-Repair advanced options do a total reinstall of grub to get correct version.

One disadvantage if BIOS boot is that you only have one MBR. Or only one system controls booting. And grub only boots working Windows. So make sure you have a separate flash drive with Windows repair console to make Windows repairs. And keep Boot-Repair/Ubuntu live installer for Ubuntu repairs.
If you have UEFI, you can always directly boot all systems from UEFI.

Windows 8 or 10 will turn on fast start up with updates and then grub will not boot it.

---

### Post by alex55555 on 2018-10-08
I don't have windows on my hard drive, only Ubuntu. Secure boot turned off, boot repair utility already runed and report from this in my first post. I use Linux for the first time. Please help me to fix the problem - I don't understand what is uefi, grub etc. What I need to do? 1) ... 2) ... 3) ... I read many topics in this forum, but they about multi system boot - I have one system installed, and I last 2 days reinstalling different versions of lububtu and ubuntu, searching for one, working with my hardware without bugs... Please, help me to end this horror.

---

### Post by yancek on 2018-10-08
You have two windows partitions (sda5 and sda6) so are those just data partitions?

You have a mix of Legacy and UEFI installs which is shown by boot code in the Master Boot Record (Legacy install) and a separate EFI partitions which indicates an EFI install.  You actually have two EFI partitions on the same drive which is a bad thing.  The grub.cfg file on sda1 shows an incorrect UUID and points to a partition which does not exist as shown below, you have no sda3:

> search.fs_uuid c50b20dd-2ad7-4d52-96ea-2eb6625e6cf5 root hd0,msdos3
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

The grub.cfg file on the second EFI partition (sda9) is correct as shown below pointing to the correct partition with Ubuntu sda10 with the correct UUID:

> search.fs_uuid f1408d3d-1399-4aeb-9bde-5038bbbaf6c0 root hd0,msdos10
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

Two possible options, the first being to set the BIOS to enable Legacy/CSM boot and try rebooting.  If that works you are good.  If it does not work, disable Legacy/CSM in the BIOS then mount sda1 and delete the grub.cfg file from sda1.  Mount sda9 and copy the grub.cfg file from sda9 to sda1 and try rebooting.  Be sure to make notes of what you do and the results so you can post back with information if these attempts fail.  If this second option works, you should then delete /dev/sda9.

---

### Post by alex55555 on 2018-10-08
[**[COLOR=#000000]yancek[/COLOR]**]("https://ubuntuforums.org/member.php?u=1928724"), thanks a lot! Deleting EFI folder with grub.cfg file at dev/sda1 and coping this folder from dev/sda9 helped and now system boots fine!

---

