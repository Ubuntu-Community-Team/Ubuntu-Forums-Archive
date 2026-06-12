---
title: "Deleting /dev/sda1"
date: 2008-08-07
forum: Installation &amp; Upgrades
---

### Post by tangibleorange on 2008-08-07
If this is in the wrong place, please move it :).

I currently have one 80GB hard disk in my laptop. It has 4 partitions:

/dev/sda1: Windows Vista Recovery Partition
/dev/sda2: Windows Vista
/dev/sda3: Ubuntu
/dev/sda4: Linux Swap

I have used Ubuntu comfortably for about a year, and am now seriously considering wiping both the vista and the recovery partition (both installed by default on my laptop). Before I do so, however, I was wondering if anyone might be able to answer these questions:

1. If I delete /dev/sda1 and /dev/sda2 (in GParted) and grow the Ubuntu partition to fill the space, does a problem arise through having /dev/sda3 and /dev/sda4, but no /dev/sda1? Will it cause some kind of boot problem?

2. My BIOS has an option called "Recovery Boot" which is enabled. Does anyone know what this does and whether it is related to the recovery partition? If I delete the recovery partition, will my BIOS lock up?

Thanks very much :).

---

### Post by cdtech on 2008-08-07
You will be fine using "gparted". Afterwards you may need to update your fstab file with the correct /dev/sd?

I don't know about your BIOS....

---

