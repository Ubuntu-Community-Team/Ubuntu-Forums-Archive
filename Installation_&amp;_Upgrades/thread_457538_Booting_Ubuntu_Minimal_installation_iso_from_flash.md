---
title: "Booting Ubuntu Minimal installation iso from flash drive"
date: 2007-05-28
forum: Installation &amp; Upgrades
---

### Post by Cows on 2007-05-28
I want to boot up the Ubuntu minimal iso from my fat32 flash drive. I downloaded the Ubuntu Minimal 7.04 ISO and did the following:

```
sudo mount -o loop mini.iso /media/iso/
sudo mount /dev/sdb1 /media/disk/
sudo cp /media/iso/* /media/disk/

```

After that I tried to boot it up but it doesn't work. Doesn't give me any errors but just boots up from grub. Yes I selected to boot from flash drive from the boot up menu and I also see the flash drive blinking.

After that I tried to install syslinux and see if that worked but it didn't. I did the following:

```
sudo apt-get install syslinux mtools
sudo syslinux -sf /dev/sdb1

```

Any suggestions?

EDIT: I got the minimal cd from here:

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by Cows on 2007-05-28
bump

---

