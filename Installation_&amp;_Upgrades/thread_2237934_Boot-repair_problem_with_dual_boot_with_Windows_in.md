---
title: "Boot-repair: problem with dual boot with Windows installed in EFI mode"
date: 2014-08-04
forum: Installation &amp; Upgrades
---

### Post by tracek on 2014-08-04
Hi,  Thus far I managed to fix my ubuntu problems just by using advices found here, but time has come to post my first cry for help. Any hints will be much appreciated, since my experience with dual boot was until recently almost painless and hence not providing "learning opportunities". Finally I have some, yay...  

Setup is the following:
1. SSD 128 GB with Windows 7 64bit (installed in EFI mode) 
2. 2 TB HDD, with both Xubuntu 14.04 64bit and Windows partitions.  

What I did: I had a flawlessly working dual boot setup of Windows (on SSD) and Ubuntu (on HDD), but then I had to reinstall Windows - and hell broke loose. Could it be because Windows by default installed itself as EFI?  

MoBo: ASRock Z77 Extreme4.  

Here is a snapshot from boot-repair: [http://paste.ubuntu.com/7955454/](http://paste.ubuntu.com/7955454/)  

I tried the 'recommended' way, but to no avail. During first steps it says "The boot of your PC is in Legacy mode. You may want to retry after changing it to EFI mode". However, in my Asrock UEFI Setup Utility there is no such thing like explicitly setting EFI mode on / off in the "Boot" section.  Then at some point boot-repair asks me to execute the following:

sudo chroot "/mnt/boot-sav/sdb5" apt-get install grub-efi linux 

... although there is of course no package called "linux". Does boot-repair support 14.04? 

The procedure ends with the following error: [http://paste.ubuntu.com/7955783/](http://paste.ubuntu.com/7955783/)  

Upon boot: error: file '/boot/grub/i386-pc/normal.mod' not found 
Entering rescue mode...  

If I remove the HDD (so the one with Ubuntu) then I can start Windows.    Any advice will be much appreciated.  Cheers, Lucas

---

### Post by oldfred on 2014-08-04
How you boot install media is how it installs for both Windows & Ubuntu. UEFI & BIOS are not really compatible and once in one mode cannot switch. So you have to boot from UEFI or BIOS for system in that boot mode.

Windows 7 default install is usually BIOS, but it can be converted to flash drive and installed in UEFI mode.

But you get into type of partitioning issues.
Windows requires gpt partitioning for UEFI.
Windows and Ubuntu only boot from MBR(msdos) with BIOS.
Ubuntu will boot from gpt partitioned drives with either BIOS (with bios_grub partition) or UEFI (with efi partition).

And if drive was gpt and you install Windows in BIOS mode it does not correctly/fully convert to MBR. Then Ubuntu installer gets confused.

I do not use RAID, as SSD is pretty fast.
       Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)

Your BootInfo report shows Windows in UEFI boot mode and Ubuntu in BIOS boot mode. Would be a lot easier if both systems were in same boot mode.
And I only use gpt partitioning for all new drives even though I currently only have a system with BIOS. But then I can move drive to a new system and it its gpt with an efi (and current bios_grub) partition at beginning of drive.

I have seen one or two mixed systems. Where the Windows efi partition has Ubuntu's efi boot loader and Uubntu's / (root) is on a MBR system. I thought that did not work, and do not suggest it, but I guess it may work.

---

### Post by tracek on 2014-08-05
Thanks for prompt response.

I installed my Windows 7 Pro 64bit from a DVD and by default it went to UEFI mode. No RAID on my system

From what I read having systems with mixed modes is possible, although not recommended and challenging. Therefore I would like to use either BIOS or UEFI for both. My preference is that I do not have to reinstall either of systems, but if it is necessary then I would rather loose Windows. 

Can you advise me on what steps should I take to convert completely either to UEFI or BIOS? As explained in the post, I tried going with Boot Repair, but without success. Do I understand correctly that it could be because my Boot Repair was run from a DVD and therefore operating in Legacy mode? Many posts I read suggest that UEFI requires running from USB, but then why my Windows got installed in this mode from a DVD?

---

### Post by oldfred on 2014-08-05
I thought Windows DVD was only BIOS, but obviously not. The instructions I had seen all discussed copying DVD to flash drive and doing some updates. Perhaps version makes a difference?

But the incompatibility of UEFI or BIOS means how you boot installer is how it installs. And UEFI should show two boot options. Usually one is clearly labeled UEFI, but other may just be a label or device name. And if drive not in correct partitioning it may be converted totally erasing it.

Type of partitioning makes a difference. Boot-Repair can convert a BIOS install of Ubuntu to UEFI if you have gpt partitioning and an efi partition. Or vice-versa if you add a bios_grub partition so grub can install correctly to gpt's protective MBR.

       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

If willing to boot from one time UEFI/BIOS boot key you can have mixed boot modes. But grub can only dual boot systems installed in the same boot mode as you have booted into grub with.

---

