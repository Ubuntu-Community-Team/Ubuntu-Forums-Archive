---
title: "Kernel Upgrade causes reboot after power off"
date: 2020-02-16
forum: Installation &amp; Upgrades
---

### Post by egrpioneer2 on 2020-02-16
Can't locate solution. Please help.

current set up: 
Ubuntu 18.04.4 LTS
5.3.0-28-generic

---

### Post by rbmorse on 2020-02-16
Could be an ACPI issue.  Check you power settings in both the O/S and BIOS/EFI, particularly the one that dictates behavior after a power interruption.

---

### Post by egrpioneer2 on 2020-02-16
Thanks for your reply! Retained previous kernel 4.15 as back up and power off works fine. Also running Windows 10 on separate HDD so bios/efi not likely cause. Could be kernel upgrade issue/bug.

---

### Post by egrpioneer2 on 2020-02-22
Just ran this week's updates and the reboot after power off bug has fixed itself!

---

