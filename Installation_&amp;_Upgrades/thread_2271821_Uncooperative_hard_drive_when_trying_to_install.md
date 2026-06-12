---
title: "Uncooperative hard drive when trying to install"
date: 2015-04-01
forum: Installation &amp; Upgrades
---

### Post by Mazate on 2015-04-01
I have windows 8 installed as my primary OS on an SSD and I have a 2nd hard drive that I would like to install Ubuntu on.  My issue is that when I go to my bios, the second hard drive isn't even seen.  I couldn't change my boot order around if I wanted to because the bios only sees the SSD and the cd rom.  When I boot Ubuntu on the USB drive and try to install on the 2nd drive, it doesn't see it either.  However, I can load up gparted in the USB Ubuntu and it sees the 2nd drive.  When I have windows loaded it also sees the 2nd drive and reads and writes to it fine.  I've tried reformatting the 2nd drive and it doesn't make a difference.  It's very strange.  Any help or suggestions is most appreciated.

---

### Post by dino99 on 2015-04-02
the first thing to do is to resolve the bios issue not finding that hdd. This often mean a plugging issue on the mobo and/or a hdd settings: small hardware bridge not set as it might in case of old pata/sata (see hdd doc)

---

### Post by Vladlenin5000 on 2015-04-02
> **9d9 said:**
> the first thing to do is to resolve the bios issue not finding that hdd. This often mean a plugging issue on the mobo and/or a hdd settings: small hardware bridge not set as it might in case of old pata/sata (see hdd doc)

+1

Without it you can't proceed.

---

