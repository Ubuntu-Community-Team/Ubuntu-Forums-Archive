---
title: "Copy ubuntu installation to another hd"
date: 2006-10-08
forum: Installation &amp; Upgrades
---

### Post by Belibem on 2006-10-08
I just got a larger hd and I would like to move my workink ubuntu installation to it. Is that possible and how? I ve tried to do it by copying the root partition of the old disk to another on the new disk but I can't make fstab to work correctly.

---

### Post by dcstar on 2006-10-08
> **Belibem said:**
> I just got a larger hd and I would like to move my workink ubuntu installation to it. Is that possible and how? I ve tried to do it by copying the root partition of the old disk to another on the new disk but I can't make fstab to work correctly.

Your existing fstab will only work if the new drive is configured and connected **exactly** the same as the drive it replaces.

For example, if your existing drive was /dev/hda, it was connected as a Master IDE device on the Primary IDE channel (/dev/hdb is Slave on the Primary, /dev/hdc Master on Secondary, /dev/hdd Slave-Secondary).

If you replaced that drive with a bigger one then the new one must also be a Master on the Primary channel to again be the /dev/hda device that Ubuntu thinks it was installed on (and initially configured the fstab file with).

The easiest thing may be to use a utility (similar to Windows Ghost) to image copy your drives, and then put the new drive in the same IDE configuration as the old one.

---

### Post by Belibem on 2006-10-08
Unfortunately this is not an option for me. I need different partitions on the new disk. Can I generate a new working fstab?

---

