---
title: "I told Ubuntu to install using whole disk; what's the best way to partition now?"
date: 2011-08-13
forum: Installation &amp; Upgrades
---

### Post by SyQo on 2011-08-13
There is no partition table on the disk. When I try to use GParted to create the table, it errors because the disk is currently mounted. What's the best way to go about moving Natty to a separate partition so that I can install Lucid and later delete the Natty partition? I contemplated DBAN, but it just seems like there's a better way to go about it. Any assistance would be greatly appreciated.

---

### Post by oldos2er on 2011-08-13
You would need to run gparted from a LiveCD so that your partitions are unmounted.

If you're going to delete the Natty partition, why not just install Lucid using manual installation and create the partitions you want?

---

### Post by SyQo on 2011-08-13
Oh, I most certainly would prefer to do that. However, when I burned Lucid to a USB stick and set the BIOS to boot from it, my computer just went into standby and nothing seemed to happen. I then tried with Debian, but it simply booted Natty anyway.

---

### Post by raja.genupula on 2011-08-13
was it done successfully ? if yes then it must boot from it after setting first boot priority to it

---

