---
title: "Wrong disk is root after Natty upgrade"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by mabloom on 2011-04-30
Last night, I performed a Natty Narwhal upgrade on a 10.10 system running from a USB connected disk on a laptop with Vista on it's built-in SATA disk.  Before upgrade to 11.04, to boot Ubuntu, I would plug the USB disk in, and it would boot because I have placed it ahead of the built-in disk in the BIOS' boot order. If I wanted to boot Windows,  I would just unplug the USB disk.

After upgrading,  the system was rebooted,  and got stuck at the grub menu. No control keys, function keys or arrow keys would do anything.  The letter "e" worked to "edit" the first menu item,  but it was not really editable. The arrow keys just _inserted_ upper case letters.  I'm running under windows at the moment, so that I can write this message,  but when "e" brings up the "edit" screen",  I can see that it is setting root to "hd0,msdos2",  which is the location of the Vista partition /dev/sda2, rather than hd1,msdos1, (/dev/sdb1), the partition containing Linux on the usb disk.

Because editing keys did not work,  I was unable to fix it from within grub. 

The install did NOT modify the built in SATA disk in any way (nor would that have been desired) and windows still boots normally when the USB disk is unplugged, but it appears that the GRUB installed on the USB disk during the upgrade is trying to load things from the SATA disk (which is a pure Windows disk) rather than from the USB disk it had loaded things from prior to the upgrade.  I was guessing that one or more of the things it could not load included those things necessary to permit one to edit grub commands.

_After writing the above_
I moved the disk to another machine that I have used it on in the past. Booting from a live disk,  I was able to do a grub-install to /dev/sdb after which editing commands worked on the grub menu,  but there seem to be a number of things still messed up.   root was now set on the right disk, but the wrong partition.  Hand editing that, I get a little farther:  a message saying that a kernel needs to be loaded before initrd.  So now, I try editing one of the older entries (for an older  kernel) to use the correct partition (using grub's 'e' command) and get a boot sequence that hangs with a message from "mountall" about a problem with something called "Plymouth".  That is where I am currently stuck.

In my opinion, when doing an upgrade to the running system,  the upgrade code should make sure that the root that the currently running system is running from remains being the same root after the upgrade has completed that it was before the upgrade started. Clearly, changing the root to be on another disk (especially one that does not even contain a Linux installation!) seems a very wrong thing for the upgrade procedure to do. 

I have been keeping my Linux system on a fast portable disk so that rather than carrying a laptop with me,  I can just carry the hard disk enclosure in my shirt pocket (from one machine to another at home, or elsewhere).  But now, because of what the upgrade has done,  I cannot yet bring the system up on any machine.

Has anyone on the Ubuntu team, or elsewhere,  come up with a fix for this kind of upgrade problem?

---

