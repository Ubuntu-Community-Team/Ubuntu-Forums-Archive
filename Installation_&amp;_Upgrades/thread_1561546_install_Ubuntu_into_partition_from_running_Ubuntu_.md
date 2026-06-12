---
title: "install Ubuntu into partition from running Ubuntu system?"
date: 2010-08-26
forum: Installation &amp; Upgrades
---

### Post by robertbub on 2010-08-26
Rather than booting into a CD, or rebooting into a partition, or rebooting at all or clobbering my MBR or installing GRUB, I would like to install Ubuntu into an existing partition from an already running Ubuntu installation.

Because of my requirements, LUBI or UNetBootin would not work because it (1) overwrites the bootloader (e.g., GRUB or NT bootloader) and (2) requires a reboot for the installation.

Is this possible?  It seems like the Debian installer could just be run from the command line, but I don't know how you'd point to the right stuff (e.g., an ISO image).

---

### Post by oldfred on 2010-08-27
I know you can boot with grub2 the ISO on the hard drive. But if the partitions are both in the extended it may not work. 

Direct boot on drive:
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
[SOLVED] Using grub 2 to boot an iso off hard drive
[http://ubuntuforums.org/showthread.php?t=1535864&highlight=ISO](http://ubuntuforums.org/showthread.php?t=1535864&highlight=ISO)

Boot ISO from harddrive. To install it would have to be different partition
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

Someone posted this but I have not tried it:
If the ISO file is on the computer to be upgraded, you could avoid wasting a CD by mounting the ISO as a drive with a command like:
sudo mount -o loop ~/Desktop/ubuntu-10.04-alternate-i386.iso /media/cdrom0

---

