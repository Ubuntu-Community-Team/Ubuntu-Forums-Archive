---
title: "Two grub/multiboot related issues"
date: 2010-12-03
forum: Installation &amp; Upgrades
---

### Post by Cyber Akuma on 2010-12-03
I have a desktop and a laptop that will have different implementations of Ubuntu and therefore GRUB:

**Desktop:**
My desktop is pretty old, it doesn't even support LBA48. The problem is the OS drive is 160GB, and while the BIOS and Windows only see about 132 gigs or so, Ubuntu can see the entire disk, so I partitioned it so the Windows partition ends at the BIOS limit and gave the rest to Ubuntu (Well, I left a few megs of unpartitioned space between the Windows and Linux partitions just to be safe with that LBA thing).

In order to make this bootable, I had to install GRUB2 on the MBR (The one installed on the MBR is called Stage 1 right?) with the ata module instead of the default bios module.

Although this works, the problem is every time GRUB gets updated, it reinstalls it with the default settings, in other words, the BIOS module, so I end up with an unbootable system that I need to use a LiveCD to re-reinstall GRUB using the ata module.

Is there any way I can get it to install GRUB with the ata module instead of the bios module when it updates? And if not, can I just stop grub from being updated, but allow everything else to keep updating on my Ubuntu install?

**Laptop:**
I plan to triple-boot Windows 7, Ubuntu, and OpenSUSE on my laptop.

The problem is that Ubuntu uses GRUB2 (and I far prefer it) and OpenSuse uses GRUB1/LegacyGRUB.

I know I can just install one of them, but that means every time the kernel is updated for the one I didn't install, I have to reboot into the other OS and manually run the update-grub command or manually edit the grub.cfg (forgot what the Grub1 config file was called) so that distro is bootable again, and I would really prefer to let everything automatically update without needing me to confirm or change everything all the time (other than manually starting the update).

I heard that you can chainload, so I left a blank 128meg partition on the beginning of my drive that I plan to use for the "master" bootloader. Problem is, I don't know how to get Ubuntu and/or OpenSUSE to install their bootloader on the partition, rather than the MBR so I can chainload it.

How would I go about doing this? Getting Ubuntu to install to the logical partition they it is installed on so I can chianload them from another install of GRUB2 that is on the MBR?

Also, would be it possible to tell Ubuntu's partition install of GRUB2 to not check for other operating systems? Since the main GRUB2 will already let me choose Windows, Ubuntu, or OpenSUSE, I don't want a second set of "Windows, Ubuntu, or OpenSUSE?" options to appear when I choose one of the Linux distros, I want it to either just directly boot Ubuntu or only bring up Ubuntu options.

I know I can rename/delete those 40_os_prober, etc files, but every time GRUB is updated it would bring them back or complain about updating them.

Any ideas anyone?

---

### Post by oldfred on 2010-12-03
Grub2 does not use stage1. I do not understand how you got grub2 to work on a BIOS with the 137GB limit. Normally you have to have a /boot partition at the beginning of the drive or the entire Uubntu system partition within the 137GB limit. Then /home can be beyond the limit. How much space are you using in windows. I would just make it 100GB, make Ubuntu's system partition 20GB and the rest as /home or shared NTFS data whichever you prefer.

Grub2 does not like to be installed to a partition which then makes chainloading difficult. But old grub does not complain. I would install OpenSuse's grub to its boot partition and chainload from Ubuntu's grub2. Not sure how OpenSuse installs though.

drs305's how to's have lots of good info on grub2 & customizing grub2
Total Custom menu:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)
[http://ubuntuforums.org/showthread.php?t=1483827](http://ubuntuforums.org/showthread.php?t=1483827)

How to: Create a Customized GRUB2 Screen that is Maintenance Free.
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

OR Partial Custom menu:
I used drs305's command to limit ubuntu entries to two, turned off os_prober so it does not look for other systems and totally customized my 40_custom.
includes line to limit display to two, also hiding of windows recovery partition
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or
sudo chmod a-x /etc/grub.d/30_os-prober

Edit - I found this in my notes, you have to have grub legacy in the partition boot sector of the install or boot of the other system example is open Solaris in sdb2:
[http://ubuntuforums.org/showthread.php?t=1529658](http://ubuntuforums.org/showthread.php?t=1529658)
menuentry "OpenSolaris 2010.03 snv_134 64bit" {
    set root='(hd1,2)'
    chainloader +1

Remember grub and grub2 number partitions differently.

---

