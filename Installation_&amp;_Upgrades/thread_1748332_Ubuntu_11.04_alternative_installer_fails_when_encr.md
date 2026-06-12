---
title: "Ubuntu 11.04 alternative installer fails when encrypted partition is used"
date: 2011-05-03
forum: Installation &amp; Upgrades
---

### Post by zimek on 2011-05-03
Hi friends.

I just tried to install 11.04 from alternative CD.
I have 500G hard disk in my laptop.

60 GB for NTFS (Windows XP)
200 MB for /boot
440 GB for encrypted partition (lvm physical volume), inside of which I have two LVM logical volumes - root (436GB) and swap (4GB)

Installation process seems to be OK.
But when installation process is finished and system is rebooted, grub menu appears and then it hangs up.
I choose to boot into Linux and I see only a blinking cursor.
No kernel information, no nothing.

I tried EXACTLY THE SAME configuration with 10.10 and everything works fine. After reboot ubuntu is booting and system is working properly.
THE SAME with 11.04 hangs right after the grub menu.

Any ideas?

---

### Post by voortuck on 2011-05-04
I had the same problems.   

Tried both fresh install & network upgrade from 10.10 with same result for guided hard disk encryption.  Same result -- locks up in grub.  :(

I have a Serp7 System76 machine with an SSD.

---

### Post by zimek on 2011-05-04
Any ideas? Anyone?

---

### Post by shizow on 2011-09-09
same problem here, one can enter the passphrase in the darkness and it boots

same problem in this thread [http://ubuntuforums.org/showthread.php?t=1762702](http://ubuntuforums.org/showthread.php?t=1762702)

---

### Post by jorok_tupur on 2011-12-01
Happens to me too.

I tried installing Lubuntu 11.10 amd64 (alternate ISO from USB flash disk) with encrypted partition option by following the guide in [How to install Ubuntu 11.04 on an encrypted LVM file system]("http://www.linuxbsdos.com/2011/05/10/how-to-install-ubuntu-11-04-on-an-encrypted-lvm-file-system/"). The result after install: GRUB boot menu is OK, but after that, blinking cursor forever.

The strange thing is: when I tried to do this on VirtualBox, it works.
I don't know what went wrong, but for now, I'm sticking to regular install (no encryption, no LVM, MBR partition scheme), nothing I can do about it I guess...

---

