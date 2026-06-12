---
title: "Install Ubuntu from GRUB2"
date: 2012-05-22
forum: Installation &amp; Upgrades
---

### Post by Fixxtr on 2012-05-22
Hello, I have an old notebook; Toshiba S1800-364E. It has a working Ubuntu 10.10, and I manually updated to GRUB2(GRUB 1.98).

But today I want to update it to latest(12.04), you know the procedure, first 11.04, then 11.10 and then 12.04. But when installing update packages for 11.04, Ubuntu and computer has freezed, I waited for more than one hour but no change at screen or activity LEDs. So I force to manually shut down. And it corrupts the Ubuntu, now system don't starts-up. I can only access to GRUB2.

Now I want to install fresh and clean Ubuntu 12.04. But by the nature of this old notebook, CD-ROM is not working and BIOS is not supporting USB boot.

So I have two options: PXE network boot, which is hard, I don't want to struggle.

And starting Ubuntu setup from GRUB2. I have ubuntu 12.04 CD .iso image at HDD(at /home/lap/newinstall). And also I have vmlinuz and initrd.gz files at same directory.

How can I start a new setup from GRUB2(1.98)? 

Thanks so much for answers from now.

---

### Post by oldfred on 2012-05-22
I have not done it from just grub, but I edit grub.cfg either on a hard drive or USB flash drive.

Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
HOWTO: Boot & Install Ubuntu from the Grub Rescue Prompt 
[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)

This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

---

