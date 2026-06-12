---
title: "dmraid -&gt; No raid disks, where is my metadata"
date: 2009-12-11
forum: Installation &amp; Upgrades
---

### Post by Ralf.P on 2009-12-11
Trying to install Ubuntu on a Fujitsu Siemens Primary Econel 100 which has two 160GB Western Digital HDD set to RAID 0 with LSI Logical Embedded SATA Raid.

Followed the HowTos so far for the case that dmraid -r continuing reporting "No raid disks" and dmraid -b can clearly see the block devices.
Succeccfully recompiled and reinstalled dmraid with different offsets set via PDC_CONFIGOFFSETS in pdc.h.
But dmraid still reporting "No raid disks". Am I doing wrong? :confused:

This are the sectors I found on which I thought that they contain the metadata.


```
00000000  53 42 42 4d cb 01 00 00  00 00 00 00 00 00 00 00  |SBBM............|
00000010  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
00000800  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00048000  00 50 60 e2 00 00 00 00  00 00 00 00 00 00 00 00  |.P`.............|
00048010  53 41 54 41 00 00 00 00  00 00 00 00 00 00 00 00  |SATA............|
00048020  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00048030  00 00 00 00 03 00 00 00  00 00 00 00 00 00 00 00  |................|
00048040  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000480b0  00 00 00 00 03 00 00 0e  00 00 00 00 00 00 00 00  |................|
*
000480f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000481f0  24 5f 45 4e 51 24 0f 33  31 00 00 00 00 00 00 00  |$_ENQ$.31.......|
00048200  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00048400  24 58 45 52 52 24 11 0d  01 26 00 00 00 00 00 00  |$XERR$...&......|
00048410  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00048600  24 5f 49 44 45 24 da 33  31 01 08 40 00 00 00 00  |$_IDE$.31..@....|
00048610  10 00 00 00 02 01 00 00  00 00 00 00 00 00 00 00  |................|
00048620  00 40 9e 12 00 00 00 00  00 00 00 00 00 10 00 00  |.@..............|
00048630  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00048790  00 40 9e 12 00 00 00 00  00 00 00 00 00 00 ff 00  |.@..............|
*
000487b0  00 00 00 00 00 00 ff 00  00 00 00 00 00 00 ff 00  |................|
*
000487d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000487f0  00 00 00 00 00 00 00 00  40 89 2f 0e 00 00 00 0d  |........@./.....|
00048800

```

Am I all wrong or is there a clue which I havent used?

---

### Post by madverb on 2009-12-11
Have you created the RAID from in the RAID BIOS on startup?

---

### Post by Ralf.P on 2009-12-11
> **madverb said:**
> Have you created the RAID from in the RAID BIOS on startup?

Yes, the RAID was build with the RAID BIOS on startup. There is an existing windows OS and two NTFS partitions (primary and extended) on it. Windows recognise the RAID and work on it with an extra driver from the PC vendor.
A third partition for Ubuntu still remains empty. Do I have to look for a extra Linux-driver or is dmraid supposed to coop with it as it is?

---

### Post by darkod on 2009-12-11
Did you use the alternate install cd? That's what you're supposed to use for LVM and/or RAID.

---

### Post by Ralf.P on 2009-12-11
> **darkod said:**
> Did you use the alternate install cd? That's what you're supposed to use for LVM and/or RAID.

I used the alternate CD once, but canceled the installation when the existing RAID wasn't recognised. I had the coise to create a RAID, but as I didn't want to destroy the existing system and data, I quit at that point.
Have I missed any options?

The most of the time I booted the live CD and worked on a memory stick, trying to get dmraid to recognise the RAID.

---

### Post by darkod on 2009-12-11
> **Ralf.P said:**
> I used the alternate CD once, but canceled the installation when the existing RAID wasn't recognised. I had the coise to create a RAID, but as I didn't want to destroy the existing system and data, I quit at that point.
Have I missed any options?

The most of the time I booted the live CD and worked on a memory stick, trying to get dmraid to recognise the RAID.

I haven't installed on raid yet, I only know you need to use that cd. If you proceeded it might have created raid on the available space, but I can't be sure of that. I understand your point, if the raid array is already created, I also thought it would see it.

---

