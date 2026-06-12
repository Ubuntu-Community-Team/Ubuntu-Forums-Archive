---
title: "Dual Booting with Windows XP"
date: 2008-07-08
forum: Installation &amp; Upgrades
---

### Post by forbzie22 on 2008-07-08
Hi,

Last night i installed ubuntu onto a laptop running windows XP SP3. On the ubuntu partitioning install menu i selected "Guided" to repartition my drive, 40GB for XP and 20GB for Ubuntu.

Everything looked ok and ubuntu installed fine.

After rebooting my laptop the GRUB boot loader loaded but Windows XP was no longer available, any ideas where it went as i selected guided install and left space for both OS's.

After booting into Ubuntu and scanning the disks i noticed that ubuntu used the whole drive !!!!! lol it wiped out windows XP.

Ive installed ubuntu, mandrake, redhat before so have a fairly good understanding of boot, root and swap partitions etc.... but never seen this before.

---

### Post by overdrank on 2008-07-08
> **forbzie22 said:**
> Hi,

Last night i installed ubuntu onto a laptop running windows XP SP3. On the ubuntu partitioning install menu i selected "Guided" to repartition my drive, 40GB for XP and 20GB for Ubuntu.

Everything looked ok and ubuntu installed fine.

After rebooting my laptop the GRUB boot loader loaded but Windows XP was no longer available, any ideas where it went as i selected guided install and left space for both OS's.

After booting into Ubuntu and scanning the disks i noticed that ubuntu used the whole drive !!!!! lol it wiped out windows XP.

Ive installed ubuntu, mandrake, redhat before so have a fairly good understanding of boot, root and swap partitions etc.... but never seen this before.

Hi and could you post the output of the command 
```
sudo fdisk -l

```that is a lower case L
and we can see if the XP partition is still there.

---

