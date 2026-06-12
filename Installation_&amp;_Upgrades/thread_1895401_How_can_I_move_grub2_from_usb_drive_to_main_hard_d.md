---
title: "How can I move grub2 from usb drive to main hard drive?"
date: 2011-12-14
forum: Installation &amp; Upgrades
---

### Post by DanWebb314 on 2011-12-14
I am a Linux novice and have installed Ubuntu Linux 11.10.  At the start of the installation, I had a “My Book” external USB hard drive plugged in.  The end result was that both Grub2 and Linux got installed on the USB hard drive.  Now I can’t boot up either Windows 7 or Linux unless the USB hard drive is plugged in.  Sometimes the USB hard drive does not get up and running fast enough and I get a “grub rescue>” error.  After 4 or 5 scary attempts, it will finally boot.  Is there any way I can move Grub over to the internal hard drive?  From the “grub rescue>”, what kind of commands need to be typed to boot either Windows or Linux?

---

### Post by dabl on 2011-12-14
Here's a nice "how to" -- don't worry it is the same for Ubuntu and Kubuntu:  [http://kubuntuforums.net/forums/index.php?topic=3106368.0](http://kubuntuforums.net/forums/index.php?topic=3106368.0)

You want Section 4.  You don't move Grub, you simply install it where you want it.  So you need to install it to the MBR of your internal hard drive.

---

### Post by oldfred on 2011-12-14
Welcome to the forums.

Will you always have your external with your system? If not installing the grub2 boot loader to the internal drive will not let you directly boot Windows. Most keep the Windows boot loader on the internal and have grub2's boot loader on the external.

Do you have external power for the external drive? Some system just do not have quite enough power from the USB port for a external hard drive.

Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

If grub is correct & it is just slow coming up this config file boot may work:
Manual boot:
grub rescue:
ls # Do you see (hd0), (hd0,1), (hd1,5) ? If so, run the next command. If you see (hd1,5), use that instead of (hd0,1) in the next command.
configfile (hd1,5)/boot/grub/grub.cfg

You do need to know partition, this is hd0,2 & sda2 your will be hd1Y and then the partition number Y your install is in. drive will be sdbY.
set prefix=(hd0,2)/boot/grub
set root=(hd0,2)
linux (hd0,2)/vmlinuz root=/dev/sda2 ro
initrd (hd0,2)/initrd.img
boot

---

### Post by DanWebb314 on 2011-12-16
This just occurred to me.  Suppose, I restore my MBR to its original state where it boots Windows 7.  Then If the USB is unplugged, Windows will boot.  If it is plugged in, the Grub screen will load as before and I will be able to boot either Windows or Linux.  Will this solution work?

---

### Post by oldfred on 2011-12-16
That is how most with removable drives configure their systems. If in BIOS you set external to boot first and it is not found it should default to the internal & just boot Windows. If the external is found then grub2 gives you a choice of which to boot.

You can restore the Windows boot loader:

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If you have grub2's boot loader in the internal you need to install it to the external first. Just boot into Ubuntu and run this, but you should update the internal parameter on where grub reinstalls to on updates:

#reinstall from working (not liveCD) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub

#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

Confirm that you can boot the external drive from BIOS or one time boot key. Then update to add Windows boot loader to internal drive, probably sda.

Another set of instructions:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive)

---

### Post by DanWebb314 on 2011-12-21
I am going to have the mark this as solved even though I have not tried out the solution.  Right now I don’t have the time and the courage to implement the solution. This link from the above reply seems to be the easiest to understand. 
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive)

I think I understand how to do it, but I don’t have complete confidence.  One mistake and I would have to get professional help.

---

