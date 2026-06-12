---
title: "Unable to boot Win 7, but can boot ubuntu. EFI partition corrupted?"
date: 2014-01-15
forum: Installation &amp; Upgrades
---

### Post by kumeyaay.nw on 2014-01-15
Hello, I'm having a problem with my dual-boot setup of Win 7/64 and ubuntu 12.04. After researching and trying several online solutions, including Boot Repair for the last several weeks, I am "head-shakingly" stumped.

Below is the link to my most recent attempt at fixing my problem using Boot Repair. By the way, I have tried both the Win 7 Repair and Installation disks. I hope someone more tech-savvy than myself can help.

Thank you so much,

Nathan

[http://paste.ubuntu.com/6759637](http://paste.ubuntu.com/6759637)

---

### Post by oldfred on 2014-01-16
You can only have one efi partition. You have two. Remove boot flag from sda3.

With BIOS/MBR you do put a boot flag on the Windows partition with boot files, but with UEFI/gpt the boot flag is only on the efi partition.

Windows 7 will not work with secure boot, but it looks like you installed the Ubuntu secure boot versions. You need to consistently boot in UEFI mode with secure boot off.
You also show a Windows boot loader in the gpt protective MBR. That will never work with gpt partitioning. Windows only boots from gpt partitioned drives with UEFI. It will not be used, but do not try to boot in BIOS mode or you will just get boot errors.

Test install of 12.04.4? That will not be official for another few weeks.

Not sure about Windows 7 repairs with UEFI. Default install is usually BIOS, but flash drive install can be configured to install in UEFI mode as you have done. Only a few vendors, just before Windows 8 came out did install Windows 7 in UEFI mode.

       Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---

### Post by kumeyaay.nw on 2014-01-18
oldfred, thank you kindly for your reply. I'll remove the boot flag from sda3 per your advisement.

As far as the Secure Boot, I'm certain I don't remember seeing anything regarding that feature in the BIOS setup, nor during power-on and boot-up at any time. Hm, my boot configuration in my (very simple) BIOS Boot tab shows "UEFI Boot [Enabled]", and "Launch PXE OpROM [Disabled]", along with "Boot Option Priorities", "CD/DVD ROM Drive BBS Priorities," then "Add New Boot Option" and "Delete Boot Option," but no Secure Boot.

I'm not certain how I ended up with two EFI partitions. That deserves another 'hm...' 

Would Gparted be suitable for removing the boot flags, or what do you suggest? I'm not sure what to do with the Windows bootloader in the gpt protective MBR. I ran wubi from w/in Win 7, and what my posted link here showed is the end result of my using GRUB, Boot Repair, et al, to untangle the mess that wubi started; after wubi I had ubuntu but no Win 7. My initial look into my hdd partitions showed a small grub_bios partition, but after running Boot Repair's "Fix Common Problems," or whatever it was, the grub_bios partition was gone, and when I rebooted I got the dreaded GRUB black screen with ">" cursor. After several tries I finally got a stable ubuntu boot and installation.

Presently ubuntu 12.04 is running fine--I mount the Windows partition when using ubuntu, and have a great deal of access to my files, but I still have a need (professionally) to be able to boot into it so that I can run AutoDesk, AutoCAD, Fusion, etc. Is there a way to repair/rebuild the Win 7 EFI partition and make it bootable without the Win 7 Install or Repair disks (they weren't much help) ? Or is my Windows boot partition essentially toast? 

No matter what the outcome, I thank you for taking the time to reply and explain what is happening on my end--I really do appreciate it, and I thank you. :)

Nathan

---

### Post by oldfred on 2014-01-18
You can use gparted to remove boot flag. 

I did not think Ubuntu installed in secure boot mode unless that was on. But if system was Windows 7 with UEFI it may have an early UEFI that did not have secure boot setting.

wubi does not work with gpt partitioned drives and is being discontinued. A bios_grub partition is used by grub2 on gpt partitioned drives when installed in BIOS boot mode. Not required or used if UEFI boot.

Your system is UEFI for both Windows & Ubuntu. You need to consistently boot in UEFI mode not BIOS/CSM mode.

You need settings correct in UEFI/BIOS to UEFI boot. But this shows boot screens so you do know which mode you have booted in.
       Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Grub can only boot working Windows, so you probably have to run Windows repairs from a Windows repair flash drive. Often chkdsk, but others also may be required. How did you resize Windows NTFS partition? Best to use Windows disk tools and reboot as after any resize Windows requires a chkdsk. You cannot run chkdsk from Linux, but some third party Windows repair disks may run a chkdsk.

---

