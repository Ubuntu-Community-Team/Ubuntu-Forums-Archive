---
title: "Dual Boot wont work"
date: 2006-10-29
forum: Installation &amp; Upgrades
---

### Post by scotty76uk on 2006-10-29
I am trying to dual boot Ubuntu with windows 2000 but computer just boots into windows 

My configuration is this

SCSI 0: Windows 2000
SCSI 1: Ubuntu

IDE Primary Master: Spare Drive
IDE Primary Slave: Spare Drive

IDE Secondary Master: DVD ROM
IDE Secondary Slave: CD Burner

I have installed Ubuntu fine and can be seen in Windows computer management, When I boot up computer just boots straight into windows I dont get any grub menu as if unbuntu is not installed atall. Any Ideas?:-k

---

### Post by kidders on 2006-10-29
Hi there,

You should make sure your primary boot device is the one with Grub on it.

---

