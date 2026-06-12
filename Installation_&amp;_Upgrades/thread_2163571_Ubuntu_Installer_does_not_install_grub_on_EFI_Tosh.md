---
title: "Ubuntu Installer does not install grub on EFI Toshiba Sattelite L955"
date: 2013-07-18
forum: Installation &amp; Upgrades
---

### Post by wubiNathan on 2013-07-18
I have a EFI comptuer with Windows 8 Pro preintalled.  I want to dualboot Ubuntu with windows, and I am pretty sure windows 8 boots on GRUB, so I instal ubuntu in another partition on my hard disk (i have no other choice, the installer did not recognize windows) and I reboot.  No GRUB.  Ubuntu does not have a bootloader entry, so the EFI bootloader would not work for me.

I am extremely confused.:confused:  And this is not a duplicate (I checked)

---

### Post by oldfred on 2013-07-18
Please go thru all the info in the link in my signature. Particularly this link.
       Shows install with screen shots.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

  [SOLVED] Can't install Windows 8 & Ubuntu in Toshiba Portege Z930 with explanation how by OP feb 2013
[http://ubuntuforums.org/showthread.php?t=2114290](http://ubuntuforums.org/showthread.php?t=2114290)

Then post link to BootInfo report.

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Install with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by wubiNathan on 2013-09-24
[COLOR=#000000]"Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot"

Got it correct.  Boot Repair gave me a grub meny and allowed both my systems to run.

Thanks,
Nathan[/COLOR]

---

