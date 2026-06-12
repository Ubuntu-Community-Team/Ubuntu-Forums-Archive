---
title: "grub grief"
date: 2007-09-15
forum: Installation &amp; Upgrades
---

### Post by fallenfantasyx on 2007-09-15
I installed ubuntu and when i booted i got the dreaded grub error 22, so obviously i went and did the fun fixmbr in recovery console.

my question, how can i get linux to load i dont care if its grub or ntldr just dont wanna go through install again, i CAN access my partitions in xp with EXTIFS

---

### Post by Pumalite on 2007-09-15
[http://users.bigpond.net.au/hermanzone/p15.htm#22](http://users.bigpond.net.au/hermanzone/p15.htm#22)

---

### Post by fallenfantasyx on 2007-09-15
should i boot live cd and do it in rescue or use super grub disk?

---

### Post by Pumalite on 2007-09-15
Boot from Super Grub.

They can easily cure that by overwritting the existing GRUB IPL code with code for another bootloader in another operating system.
In other words either re-install GRUB or re-install Windows bootloader or some other bootloader or boot manager. In Super GRUB Disk, go 'English Super Grub Disk'-->'Windows'-->'Fix Boot of Windows', or see my 'Un-install Page'.

Re-install Grub: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by fallenfantasyx on 2007-09-15
thank you very much ill take care of that soon as i find a blank cd :D

---

### Post by Pumalite on 2007-09-15
You are welcome. Good luck.

---

