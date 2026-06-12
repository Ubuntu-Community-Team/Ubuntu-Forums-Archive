---
title: "Via Raid"
date: 2005-03-26
forum: Installation &amp; Upgrades
---

### Post by Ryujin on 2005-03-26
Can I pass something to the kernel that will allow me to see my sata raid array in the install?

---

### Post by alastair on 2005-03-26
Maybe not. But you would have to detail the hardware and setup more i.e. model of controller etc.

Many cheap(ish) SATA controllers do s/w RAID, but use functionality only available to Windows. This is generally no big deal, because Linux has good s/w RAID built in. However, if the disks have already got data on them, this is a problem. Linux sees 2 disks (say), not one volume - and you'd use Linux to RAID.

As I said, depends on your hardware though .... which you did not specify.

---

