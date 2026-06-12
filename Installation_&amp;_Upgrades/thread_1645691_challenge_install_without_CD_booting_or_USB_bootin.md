---
title: "challenge: install without CD booting or USB booting"
date: 2010-12-14
forum: Installation &amp; Upgrades
---

### Post by admaw11 on 2010-12-14
I have a desktop pc (P3 1.4ghz)
-it does NOT support booting from USB

-the CD drive is a little old and seems to get read errors

-it CAN boot off the ubuntu CD however installing from it seems to result in read errors and corrupted install etc - however the same disc has installed to other machines successfully.

-the PC's USB ports do work fine and ubuntu can read them when booted via the CD. (just does not support booting from USB)

-The BIOS does say it can boot off LAN, but I've never tried this, but I do have network cable and laptop and netbook with ubuntu bootable and installed on.

I have a bootable USB key which boots ubuntu fine and installed it to the netbook fine.

possible approaches I could take are:
-somehow force the install to run from the USB after the machine has booted off the CD (ubuntu has occasionally reported errors / crashes while booted from the dodgy CD drive)

-boot off a network connection to the netbook with ubuntu installed - unsure if this is possible / how it works.

-directly copy the content of the USB stick to a partition on the drive and try to make it boot from there.

-directly copy an installed partition from one of my other systems onto a partition on this PC's drive.

any suggestions as to which of these approaches might work, or any other suggestions?

regards.

Adam.

---

### Post by oldfred on 2010-12-14
You can just install hard drive to another system and install from that system. As long as you do not install special drivers, particularly video you will then be able to move it back.

If you have a spare partition you can boot from, then you can mount the ISO from that partition and install to another partition. 

Direct boot on hard drive:
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

The plop boot manager supposed works.
Boot USB or PCMCIA (new)
[http://www.plop.at/en/home.html](http://www.plop.at/en/home.html)

You can install grub2 to a CD with just a kernel to boot and then chroot into the USB to boot that.

Link really on for grub2 boot.
Herman has instructions for grub2 rescue boot CD, USB, or floppy. Also grub legacy
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB2_CD-ROM](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB2_CD-ROM)

---

### Post by admaw11 on 2010-12-15
yeah looks like plenty of options now, I think that Plop boot manager will work for me.
So much for thinking I'd have to learn about booting from the NIC.

---

