---
title: "Installation OK, but the bootloader isn't there"
date: 2013-08-02
forum: Installation &amp; Upgrades
---

### Post by skamarla on 2013-08-02
I have just installed Kubuntu in an HP netbook (details in [this thread]("http://ubuntuforums.org/showthread.php?t=2162106")). The root wil be in the SSD (/dev/sdb), and /home and swap in the HDD (/dev/sda). Windows 7 is also there.

After a clean installation (no errors, no warnings), when I reboot, Windows starts up directly. No grub screen, no options, nothing. I have tried both installing the bootloader in /dev/sda and /dev/sdb, but it makes no difference. The BIOS only gives you the option of booting from the HDD (that would be /dev/sda).

Any ideas?

---

### Post by GwL3eNC on 2013-08-02
Hi,

i dont want to be guilty if something goes wrong, but if you want grub is the bootloader
you must install it in the master boot sector of you hard drive. Have you done that?

WARNING: you possibly could overwrite the win loader and then without a boot cd nothing goes.

The grub-customizer from 

[https://launchpad.net/~danielrichter2007/+archive/grub-customizer](https://launchpad.net/~danielrichter2007/+archive/grub-customizer)

can symplify things for you. He has the file menu option to install grub in MBR.
Be carefull.

---

### Post by grahammechanical on 2013-08-02
The BIOS may be seeing the SSD as a removable drive and so looking at the usual hard drive options does not show the SSD. You may need to look elsewhere. I assume that the SSD is connected when you open the BIOS. What do you mean when you say "I have tried both installing the bootloader in /dev/sda and /dev/sdb?" How?

We usually do that from a working Ubuntu but you cannot boot into Ubuntu? You may have installed Grub to the MBR but is it connected to grub.cfg in sdb /boot/grub?

I have found that the Ubiquity installer defaults to installing Grub into sda. So, the default should be giving you a grub menu when the BIOS searches sda for an operating system.

You might find boot repair useful

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Regards.

---

### Post by skamarla on 2013-08-02
I had tried to do it by reinstalling Kubuntu again and again, to no avail.

Boot-repair did it. I just started the Live CD, apt-got boot-repair, ran, and it works. Thanks!

---

