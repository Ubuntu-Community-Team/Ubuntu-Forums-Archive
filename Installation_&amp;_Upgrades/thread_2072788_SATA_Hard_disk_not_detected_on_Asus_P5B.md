---
title: "SATA Hard disk not detected on Asus P5B"
date: 2012-10-18
forum: Installation &amp; Upgrades
---

### Post by chribonn on 2012-10-18
Hi,

I have an Asus P5B computer with a Maxtor 320GB SATA hard disk. Unfortunately neither Ubuntu 12.04 nor 11.10 install disks are able to detect the hard disk. Nothing comes up in the dialogue box "Installation Type" of that part of the installation where you are expected to partition the hard disk.

I successfully installed and ran Windows 7 and Windows XP on this same computer. gParted also sees the disk and allowed me to clear existing partitions and format it as ext4 (I read somewhere that this might kick start Ubuntu installation into recognising the disk. It did not work.

In Asus's BIOS (latest for the M/Board) I tried both ACPI as well as standard IDE; again without any success.

Any help would be greatly appreciated.

---

### Post by chribonn on 2012-10-19
I figured out a solution that, although long winded worked for me if you are desperate.

1. Install Ubuntu on another computer.
2. Use a product to image the hard disk (I use Acronis).
3. Restore the image you had taken.

Ideally the installer should work.

> **chribonn said:**
> Hi,

I have an Asus P5B computer with a Maxtor 320GB SATA hard disk. Unfortunately neither Ubuntu 12.04 nor 11.10 install disks are able to detect the hard disk. Nothing comes up in the dialogue box "Installation Type" of that part of the installation where you are expected to partition the hard disk.

I successfully installed and ran Windows 7 and Windows XP on this same computer. gParted also sees the disk and allowed me to clear existing partitions and format it as ext4 (I read somewhere that this might kick start Ubuntu installation into recognising the disk. It did not work.

In Asus's BIOS (latest for the M/Board) I tried both ACPI as well as standard IDE; again without any success.

Any help would be greatly appreciated.

---

