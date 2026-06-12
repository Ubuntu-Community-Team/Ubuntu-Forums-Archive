---
title: "Problem with boot"
date: 2008-06-22
forum: Installation &amp; Upgrades
---

### Post by *Genom* on 2008-06-22
Pls I need help...I have earlier ubuntu (4.10 - 7.04), but now when I will install newly ubuntu 8.04 (32 or 64 bit),in boot ubuntu freeze...

In recovery mode it writte me either -> hardware abstraction layer or GNOME display manager and then freeze...

MB:Asus M2N
CPU:AMD X2 3800+
Graphic Card:GF 7600 GS 512 MB
RAM: A-Data 2x512,2x1024 MB
HDD:Seagate Baracuda 40GB ATA
    Samsung 360 GB SATA II (in instalator SCSI)

---

### Post by *Genom* on 2008-06-23
Nobody knows? :(

---

### Post by ssican on 2008-06-23
See: Verifying the CD/DVD Integrity
 [https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)

EDIT:
1)- BurningIsoHowto:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

2)- HowToMD5SUM:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

3)- Burn the .iso image on speed 4X

---

### Post by *Genom* on 2008-06-23
problem is solved...

be enought edit grub and enter arguments noapic and acpi=off

---

