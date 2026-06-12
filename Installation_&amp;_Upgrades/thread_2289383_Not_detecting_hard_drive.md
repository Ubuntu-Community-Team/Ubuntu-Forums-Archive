---
title: "Not detecting hard drive"
date: 2015-08-03
forum: Installation &amp; Upgrades
---

### Post by rick47 on 2015-08-03
Hey all. I have a Dell Latitude e6510, which I'd like to install Ubuntu Mate on. I want to completely get rid of Windows 7.

My drive isn't being detected though. Not by the installer, gparted, or fdisk. They only detect the USB drive that I want to install from.

I changed the SATA setting in the BIOS from RAID to AHCI and that hasn't made a difference. I did a complete system restore on windows as well.

Anyone have any ideas? This is my first time giving linux a try, so apologies for being clueless.

---

### Post by rick47 on 2015-08-04
Anyone? Please?

---

### Post by sudodus on 2015-08-04
Welcome to the Ubuntu Forums :-)

Do I understand correctly?

- You have an internal hard disk drive, and you want to install Ubuntu Mate into it.

- You can boot into a live session from a USB drive, and the live system seems to work well.

Is Windows still working in the computer?

Can you see any sign of life from the HDD, for example in the BIOS menus, or hear a noise from it?

Normally a healthy drive would show in the output of the following commands (at least as the device itself, maybe not any partitions). Please run them from a terminal window and post the output in a reply! Maybe the connection is bad, (try to remove it and put it back again)!

```
sudo parted -ls
```

```
sudo lsblk -fm
```

---

