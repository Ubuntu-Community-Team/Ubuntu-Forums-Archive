---
title: "Need Help with 10.04 LTS Install on a Intel D865GBF mobo"
date: 2010-06-04
forum: Installation &amp; Upgrades
---

### Post by kuttysark on 2010-06-04
**So the specs are as follows:**

Video Card: ATI 9800 Pro 128mb
CPU: Intel P4 3.2ghz HT
RAM: 4 x 512mb DDR 400 dual channel
HDD: 2x Sata I 80 GB (Seagate Baracudda's)
MOBO: Intel D865GBF
PS: 450 Watt Generic
WIFI: Zyxel M202 Mimo G (works from get go with live CD Ubuntu)

Ubutnu 10.04 LTS x86 32 bit disc

**So my Issue:**

When I boot up linux from live disc, it loads and runs fine.  Gparted and Disk Utility see my drives as seperate entities  When going to install to HDD, it detects my Sata HD's as RAID 0 or JBOD array (one massive drive) instead of as seperate ide drives.  IT lists it as 

*"Serial ATA RAID via_bhgfgcgija (linear) - 160.1 GB Linux device-mapper (linear) "*

If I continue with install, it jumps to 5% install and says 

*"The ext4 file system creation in partition #1 of Serial ATA RAID via_bhgfgcgija (linear) failed."*

I suspect that it's the incorrect HD controller since the HDD's are in IDE mode (no bios option for raid)


Any help would be appreciated.  Maybe even a how to on how to change the driver (which it doesn't seem to give me an option to change).

Thanks for any help/light you guys can shed on the subject.

~Kuttysark

---

### Post by kuttysark on 2010-06-04
okay, so I found if I disconnect one of the HD's and preform the install things run smoothly.  I will let you know what happens when I reconnect the second drive after install!

---

