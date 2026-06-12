---
title: "Bootloader on wrong HDD"
date: 2008-08-24
forum: Installation &amp; Upgrades
---

### Post by biblefreak on 2008-08-24
Never had this problem with any other distro, so this is a first for me. Installed Ubuntu Hardy and LOVE it. Have always been into KDE, but I digress. For some reason my bootloader installed on my ide drive rather than my SATA drive. My current setup is a 250gb SATA with half allocated to Windows and shared partitions and the other half to Linux and a swap partition. My ide drive is only there because I haven't taken it out!! With my BIOS set to boot from SATA I get GRUB errors, presumably from my old pcLinuxOS partition I wiped out to install Ubuntu. If I change BIOS to boot from the ide drive, Grub loads fine and I can select my Windows or Ubuntu installs.

How do I correct this issue as I am fixing to pull the ide drive to put in another machine?

---

### Post by Pumalite on 2008-08-24
Pull the IDE drive and then reinstall Grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by sandysandy on 2008-08-24
u can try Super Grub Disk also, after disconnecting ur ide drive.

regards

---

