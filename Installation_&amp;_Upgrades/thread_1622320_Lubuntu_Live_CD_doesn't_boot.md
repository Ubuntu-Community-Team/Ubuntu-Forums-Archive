---
title: "Lubuntu Live CD doesn't boot"
date: 2010-11-15
forum: Installation &amp; Upgrades
---

### Post by AlFrugal on 2010-11-15
I downloaded the Lubuntu 10.10 Live-CD ISO and burned it to a CD-RW disc. The Lubuntu Live-CD fails to boot on my secondary PC. It boots fine on my primary PC.

The PC on which Lubuntu fails to boot is a Dell Dimension L (year 2000). Celeron 566 MHz. 192 MB RAM. That PC has Xubuntu 10.10 installed on HDD. Xubuntu runs fine.

The PC on which Lubuntu boots OK is a Dell Dimension 4100 (year 2000). PIII 733 MHz. 512 MB RAM.

The failing boot progresses to a point where I get a purple screen showing "Ubuntu 10.10". Underneath the "Ubuntu 10.10" is a progress bar consisting of four dots. The progress bar continually shows progress, but after a few minutes there is no HDD or CD activity. After about seven minutes I get a blank bluish-gray screen. After waiting an additional five minutes I pressed "Enter" and was returned to my original purple screen. The progress bar continued to show progress, but there was no HDD or CD activity.

The Release Notes for Lubuntu 10.10 indicate that my secondary PC has sufficient RAM.

---

### Post by dino99 on 2010-11-15
try with noacpi (F6) when installing

---

### Post by AlFrugal on 2010-11-15
> **dino99 said:**
> try with noacpi (F6) when installing

I tried your suggestion. Twice I booted with ACPI=OFF. A third time I booted with ACPI=OFF and NOAPIC. All three times the boot behaved the same as in my original post.

---

