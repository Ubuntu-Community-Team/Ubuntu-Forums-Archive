---
title: "GRUB does not show Windows any ideas?"
date: 2015-04-08
forum: Installation &amp; Upgrades
---

### Post by arbiter2 on 2015-04-08
Hey guys, hope you're doing well...

I've got a problem with GRUB, I'm using Intel’s raid software and got a 256GB/256GB raid disk with windows 8.1 installed, got a new M.2 drive with Ubuntu, the problem is GRUB creates a menu without Windows and I tried solving it using boot-repair but that does'nt change a thing. (The system also has a 1TB drive for storage)

The GRUB menu is always:
Ubuntu
Ubuntu - other options (something similar)
EFI firmware (something similar)
System Setup (which just takes me to BIOS settings)

I also have the Boot info summary from the boot-repair [http://paste.ubuntu.com/10779162/](http://paste.ubuntu.com/10779162/)

Thanks ;)

---

### Post by oldfred on 2015-04-09
I do not know RAID. 

But it seems that Boot-Repair tried to add RAID drivers, but you do not seem to show efi partition for Windows.
Is Windows installed in UEFI boot mode or CSM boot mode.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

For grub to dual boot you have to install the RAID drivers, which normally are not in a Desktop install, Windows must be in UEFI boot mode, and fast startup or always on hibernation must be off in Windows.

UEFI and CSM/BIOS are not compatible, you have to totally reboot to switch modes, or you can only use grub to boot other installs in the same boot mode.

---

### Post by arbiter2 on 2015-04-09
I turned off fast startup in windows and tried it again, however I got the same problem.
I have CSM disabled in my BIOS for windows

Do you think I need the RAID drivers in the Ubuntu installation?

---

### Post by oldfred on 2015-04-09
Linux will not see the Windows without whatever RAID drivers are needed for your type of RAID.

I thought Boot-Repair added the RAID drivers for its use, but seemed to have issues seeing the RAID partitions.

 [http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)

I do not think this includes any info on UEFI versions:

 parted (3.0) completely removes filesystem creation and modification support, except for filesystem probing to determine what's in a partition.
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
User who installed fakeRAID
How to install Ubuntu 14.04 in software RAID 1 with Intel Z87 chipset mobo controller
[http://ubuntuforums.org/showthread.php?t=2229126](http://ubuntuforums.org/showthread.php?t=2229126)

---

### Post by arbiter2 on 2015-04-10
So I had a go with this again however I noticed that when running boot repair, I get the windows partition in the launcher and if I try to click on it I get this error:
[IMG]http://i.gyazo.com/82011f13d0f2e682fd69e252448991cf.png[/IMG]
so I guess for some reason the system is always on, although fast startup is turned off o.O

Thanks for the help oldfred!

Edit: At the moment I get to switch between the two OS's via the BIOS where i can select which drive to boot from which I guess i can live with

---

