---
title: "Reinstall Ubuntu but leave boot loader alone"
date: 2008-09-06
forum: Installation &amp; Upgrades
---

### Post by thegnark on 2008-09-06
Hello, I currently have Vista and Ubuntu installed, with Vista's boot loader handling initial OS selection. If I select Ubuntu, it then kicks me over to GRUB...

My question is, if I want to reinstall Ubuntu into the same partitions but not mess with my boot loader setup, what do I need to do special during (re-)installation?

---

### Post by Pumalite on 2008-09-06
Install on top the old Ubuntu partitions and install Grub to it's 'root' partition. Then do what you did before to boot Ubuntu with Vista. You can ignore /swap

---

### Post by thegnark on 2008-09-06
i guess my question, more specifically, is at what point in the installation do i point grub to its destination.... for all the times i've installed ubuntu i don't ever remember choosing that option...

---

### Post by Pumalite on 2008-09-06
Step 7 I think; 'Advaced Tab'. Change (hdo) for /dev/???
where ??? is the partition of your 'root'.

---

