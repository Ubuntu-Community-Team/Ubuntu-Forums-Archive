---
title: "Fat 32 partition type in Ubuntu 20.04"
date: 2020-12-10
forum: Installation &amp; Upgrades
---

### Post by gardenair on 2020-12-10
I have just installed  Ubuntu 20.04 on my 320 GB Hard Disk using a 8 GB boot-able USB . Under Installation Type  I select **" Install Ubuntu 20.04 LTS alongside Ubuntu 20.04.1 LTS "**  . Ubuntu create partition automatically and install on my hard disk.
Now I want to install according to my own partition scheme .Boot from USB to start **Install Ubuntu** I select **"Something else"** and press **" Continue "** .

Here I can view  my partition scheme as

```
[B]/dev/sda
   /dev/sda1 fat32       536 MB                  33MB
   /dev/sda5 ext4        319533 MB    15749 MB Ubuntu 20.04.1 LTS (20.04)[/B]
```

The thing which I want to ask is why Ubuntu create /dev/sda1 fat32  ? _Is there any logic to create **fat32** type behind it ?_   Is it boot partition or something else ?

2- Ubuntu create sda1 and sda5 where is sda2 ,sda3and sda4 ?

---

### Post by C.S.Cameron on 2020-12-10
It is an EFI boot partition, so that you can boot in UEFI mode.
It is there because you started your Live USB installer in UEFI mode.
If instead you start your Live USB installer in BIOS mode you won't be given an EFI partition.

---

### Post by gardenair on 2020-12-10
Well my Laptop BIOS "Boot Lisat Option" it  is set on **Legacy **.The UEFI is disable.My USB partition scheme is "MBR" and the Target system was "BIOS  (or UEFI-CSM).

---

### Post by CelticWarrior on 2020-12-10
Unless you have BIOS there's no good reason to install in BIOS mode (Legacy).
That said the new installer will create an EFI partition even in Legacy/MBR anyway.

---

### Post by grahammechanical on 2020-12-10
Do you get the Grub boot menu? Can you load either Ubuntu 20.04.1 or 20.04? Or both? If you can load a version of Ubuntu, open Disks and examine the partitions in that utility.

Regards

---

### Post by gardenair on 2020-12-11
There is no Grub boot menu.It is install  on my laoptop.It is ubuntu 20.04.1 LTS from [https://ubuntu.com/download/desktop](https://ubuntu.com/download/desktop) Can you ou guide me the disk utility name to examine the Hard Disk.

---

### Post by CelticWarrior on 2020-12-11
Try booting the already installed system in UEFI mode. If it works keep it as that IS the recommended option.
Also please describe post specifications of ALL your drives. What's shown in the OP is a single drive with Ubuntu 20.04.1. And why would you want to install another identical Ubuntu? The aforementioned "install alongside" suggests you were trying to install another one of the same, perhaps in another drive that you didn't show.

---

