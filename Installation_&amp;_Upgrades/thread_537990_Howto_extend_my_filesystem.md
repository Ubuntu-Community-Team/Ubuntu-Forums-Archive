---
title: "Howto extend my filesystem ?"
date: 2007-08-29
forum: Installation &amp; Upgrades
---

### Post by GoldWing on 2007-08-29
This is my current fdisk -l layout:


Schijf /dev/sda: 160.0 GB, 160041885696 bytes
255 koppen, 63 sectoren/spoor, 19457 cilinders
Eenheid = cilinders van 16065 * 512 = 8225280 bytes

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sda1               1         637     5116671   12  Compaq diagnostiek
/dev/sda2   *         638       10015    75328785    c  W95 FAT32 (LBA)
/dev/sda3           10016       10139      996030   82  Linux wisselgeheugen
/dev/sda4           10140       16242    49022347+   5  Uitgebreid
/dev/sda5           10140       10163      192748+  83  Linux
/dev/sda6           10164       16242    48829536   8e  Linux LVM

I still have 25.63 GB available that is not partitioned (at the end of the disk.

How can I add it in some way ? I can't add any more partitions with fdisk or gparted.

---

### Post by kellemes on 2007-08-29
> **GoldWing said:**
>  I can't add any more partitions with fdisk or gparted.

Because?
Guess because you're on your primary partition limit.. right?

---

### Post by wolfen69 on 2007-08-29
can't you just resize the partition with gparted?

---

### Post by GoldWing on 2007-08-29
Because I have already 4 full primary partitions ?
Which partition can I resize ?

---

### Post by wolfen69 on 2007-08-29
which ever one you want.

---

### Post by GoldWing on 2007-08-29
the only thing that I can do is to resize my FAT32 partitions, but that doesn't help me using the free swap with another partition.

---

### Post by merlinus on 2007-08-29
FWIW, to ensure future harmony and tranquillity, backup data and reinstall ubuntu.

That way you can leave sda1 and 2, and partition the way you wish.

And be sure to make sda3 an extended partition this time!

-merlin

---

