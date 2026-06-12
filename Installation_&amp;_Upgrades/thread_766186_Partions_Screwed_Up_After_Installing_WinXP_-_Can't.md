---
title: "Partions Screwed Up After Installing WinXP - Can't Reinstall Grub or Reinstall Ubuntu"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by GreySim on 2008-04-25
I had a dual boot setup with a beta version of Hardy and Win2k (on a FAT partition). Last night I installed XP over Win2k (games now are starting to require XP, sadly), deleting the FAT partition and formatting it to NTFS. Afterwards I just expected to reinstall grub and everything would be okay, but now Ubuntu isn't recognizing any of the partitions on that drive correctly. Does anyone know what went wrong, and how I might be able to either restore access to my existing Hardy install, or reinstall Hardy without wiping the whole disk (hope to not have to though since I forgot to backup my installed software list before upgrading to XP). I attached a few screenshots with how the various OSes and utilities see my harddrive. Windows has an ext3 driver installed; Hardy and Vault are ext3 formatted. Also, I'm not sure why it's showing two 1.1 GB partitions. I thought I only had one ~1 GB swap partition, and two OS partitions. Thanks in advance, and let me know if I can provide any more info.

[http://i59.photobucket.com/albums/g294/GreySim/partitions-windows.png](http://i59.photobucket.com/albums/g294/GreySim/partitions-windows.png)

[http://i59.photobucket.com/albums/g294/GreySim/linux-livecd-partitions.png](http://i59.photobucket.com/albums/g294/GreySim/linux-livecd-partitions.png)

[http://i59.photobucket.com/albums/g294/GreySim/grub-setup.png](http://i59.photobucket.com/albums/g294/GreySim/grub-setup.png)

---

### Post by IgnorantGuru on 2009-11-01
That's odd.  Personally, I would use SystemRescueCD to boot into a linux root.  Then reinstall grub to the MBR using the same grub commands you're using.
[http://www.sysresccd.org/](http://www.sysresccd.org/)

---

