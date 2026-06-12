---
title: "Install Meerkat alongside existing Lucid"
date: 2010-10-02
forum: Installation &amp; Upgrades
---

### Post by JohnMac on 2010-10-02
I wish to install Ubuntu Meerkat "alongside" my existing Lucid install. I "try" the new release using a Live CD and all goes well so I proceed to use the graphical interface to install. It seems to install OK and I end up with a second linux partition as shown below.

However when I reboot only my original lucid partition boots (obviously really as the asterix indicates that it is the boot partition)

How do I boot my new release? Should grub2 come up and offer me an option?

My system:
 Desktop AMD 5200 dual processor
 On board graffics
 RAM 2G
 160G IDE drive

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00075a81

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   166637785    83317869   83  Linux
/dev/sda2       166639614   312580095    72970241    5  Extended
/dev/sda5       300886016   312580095     5847040   82  Linux swap / Solaris
/dev/sda6       166639616   295319551    64339968   83  Linux
/dev/sda7       295321600   300881919     2780160   82  Linux swap / Solaris

---

### Post by agmcclard on 2010-10-02
sudo update-grub :)

---

### Post by JohnMac on 2010-10-03
I tried again, created a new partition and installed Meerkat 10.10rc into it without any problems. Then I did update-grub.:P

---

