---
title: "Hard drive issues."
date: 2006-04-10
forum: Installation &amp; Upgrades
---

### Post by Atticus on 2006-04-10
Hello

I'm a hopeful convert to Ubuntu from WinXP Pro.. Except that my WD 250 GB Sata drive isn't recognized. What can i do to get Ubuntu to install on my HDD??

---

### Post by PriceChild on 2006-04-10
Where isn't it recognising it? In the partitioning stage?

It still comes up in the bios right?

---

### Post by Atticus on 2006-04-10
It shows up in the BIOS correctly but during the partition stage its a no-show. Its very frustrating.

---

### Post by Jason_25 on 2006-04-10
Please post hardware specs.

---

### Post by Atticus on 2006-04-10
AMD A64 3000+
Asus A8v-MX mobo
512mb of Corsair value ram
WD Cavier SE16 250GB ** Problem area.. ](*,) 
GeForce MX 440

---

### Post by Atticus on 2006-04-12
Any ideas?

---

### Post by dbd on 2006-04-12
What do you mean by it's a no show. Does it show the drive, but no partitions, or does it just not show the drive at all?

If you get ubuntu live and then boot with that then you can have a look at your hard drive partitions using other linux tools.

if, at the command line you enter the command:
sudo fdisk -l 
then let us know what that says.

---

