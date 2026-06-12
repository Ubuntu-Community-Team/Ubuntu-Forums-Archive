---
title: "Cant See Drive during Install"
date: 2011-02-25
forum: Installation &amp; Upgrades
---

### Post by scpatl4now on 2011-02-25
I have a drive partitioned with 3 partitions and I want to install 10.10 on the 3rd partition.  I have partitioned and formatted the drive, but when I try to install from the Live CD, the drive does not show up.  It is attached to a SIL PCI0680 ultra ATA-133 Host controller.  I can see it in the disk utility, but not when I go to install.  Is there something I need to download before I start the install???

---

### Post by oldfred on 2011-02-25
If Disk Utility sees it, I would think the driver for it is there. Sometimes other partition issues prevent gparted from seeing a drive.

What does this show?
```
sudo fdisk -lu
```

I had a drive that booted XP ok but gparted would not see it. I ran chkdsk on the drive and then it worked in gparted.

---

### Post by scpatl4now on 2011-02-25
gparted DOES see it.  I am able to partition it as well.  Its just when I start the installer and try to manually chose the partition to install to, the disk does not show up on the list

---

