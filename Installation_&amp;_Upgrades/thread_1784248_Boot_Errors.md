---
title: "Boot Errors"
date: 2011-06-16
forum: Installation &amp; Upgrades
---

### Post by xTLx on 2011-06-16
I've dual booted my computer but ive decided to remove ubuntu now. would i run the risk of having problems booting windows if i were to delete my ubuntu partition? and would ubuntu remove its self from the boot menu after i have removed the partition that its on?

---

### Post by drs305 on 2011-06-16
> **xTLx said:**
> I've dual booted my computer but ive decided to remove ubuntu now. would i run the risk of having problems booting windows if i were to delete my ubuntu partition? and would ubuntu remove its self from the boot menu after i have removed the partition that its on?

If Grub is the controlling bootloader, you can use the Windows disks to restore the Windows bootloader and then remove Ubuntu, or in your last boot into Ubuntu (before you say goodbye to it) or from the LiveCD, transfer control back to the Windows files.

You would install lilo, an alternate bootloader, and have it point the MBR to your Windows partition. As long as the boot flag is on your Windows partition, this is fairly reliable. 
```

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
this assumes Windows is on sda. Also, disregard the messages saying to configure lilo. This isn't necessary.

If BIOS was set to a different drive, make sure you put it back to the Windows drive.

You might want to bookmark this link:
[How to restore the Ubuntu/XP/Vista/7 bootloader ]("http://ubuntuforums.org/showthread.php?t=1014708")

---

