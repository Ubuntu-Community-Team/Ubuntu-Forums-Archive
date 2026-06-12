---
title: "Upgrading from hard disk partition (Ubuntu Studio DVD .iso)"
date: 2007-11-09
forum: Installation &amp; Upgrades
---

### Post by Globox on 2007-11-09
My laptop does not have a DVD drive and Ubuntu Studio does not have a non-DVD .iso version.

I've read various guides on how to create a new partition using GParted to copy the .iso contents to, but I can never get passed step one: creating a new partition.

Whenever I launch GParted (as root or otherwise) all of the options are grayed out. I can't remove or resize any of the current partitions, nor can I create new ones.

Could someone please help me out with this? I'd really like to give Ubuntu Studio a spin.

---

### Post by logos34 on 2007-11-09
They're grayed out because mounted.  You can't resize a mounted partition.  Download the [latest Gparted live cd]("http://gparted-livecd.tuxfamily.org/") (0.3.4-10) and work from that.

---

### Post by Drunky on 2007-11-09
> **Globox said:**
> My laptop does not have a DVD drive and Ubuntu Studio does not have a non-DVD .iso version.

I've read various guides on how to create a new partition using GParted to copy the .iso contents to, but I can never get passed step one: creating a new partition.

Whenever I launch GParted (as root or otherwise) all of the options are grayed out. I can't remove or resize any of the current partitions, nor can I create new ones.

Could someone please help me out with this? I'd really like to give Ubuntu Studio a spin.

You can always upgrade from Ubuntu Gusty 7.10 to Ubuntu Studio 7.10 by following the directions given on  [this]("https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromGutsy?highlight=%28STUDIO%29") wiki page.

In a terminal, type:```
sudo apt-get update && sudo apt-get install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video linux-rt
```

---

### Post by Globox on 2007-11-13
Thank you both very much!

---

