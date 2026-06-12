---
title: "Can't get persistence working Ubuntu 14.04.2 USB stick"
date: 2015-06-23
forum: Installation &amp; Upgrades
---

### Post by markh1289 on 2015-06-23
Hi,

I used this method,
[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu)
... with 8GB USB stick to create bootable USB with 1GB persistent storage, with image,
[Ubuntu 14.04.2 LTS Desktop (64-bit)]("http://releases.ubuntu.com/14.04.2/ubuntu-14.04.2-desktop-amd64.iso.torrent")
... with an HP Elitebook 1040 (8GB RAM).
It boots and works beautifully but persistence does not work.

I used the same method with image,
[Ubuntu 14.04.2 LTS Desktop (32-bit)]("http://releases.ubuntu.com/14.04.2/ubuntu-14.04.2-desktop-i386.iso.torrent")
... with Dell D630 (2GB RAM) and persistence works.

Any hints as to what might be stopping 64bit one from being persistent would be much appreciated.

Regards, MH

---

### Post by ubfan1 on 2015-06-23
Persistence was fixed for UEFI machines in 15.04 (bug 1159016).  The problem was that for UEFI machines, grub is used instead of syslinux for booting, and the word "persistent" was not added to the grub.cfg file.  You can add it yourself by editing the file /boot/grub/grub.cfg (since for live media, no updates are expected for this file).

---

### Post by sudodus on 2015-06-23
You can also use the 'grub and iso' method according to the following posts - and get a persistent pendrive that works in (almost) all PC computers from very old to very new, with and without UEFI.

See [One pendrive for all PC (Intel/AMD) computers]("http://ubuntuforums.org/showthread.php?t=2259682") particularly

Post #6.   [A smaller and simpler pendrive for all PC (Intel/AMD) computers - 'grub-n-iso']("http://ubuntuforums.org/showthread.php?t=2259682&p=13300523#post13300523") - Lubuntu  32-bit
Post #7. [Multiboot pendrive system for all PC (Intel/AMD) computers]("http://ubuntuforums.org/showthread.php?t=2259682&p=13302264#post13302264")
Post #8. [Build your own single boot or multiboot pendrive for all PC (Intel/AMD) computers]("http://ubuntuforums.org/showthread.php?t=2259682&p=13302278#post13302278")

---

