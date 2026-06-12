---
title: "Xubuntu 7.04: &quot;acpi=force&quot; disables eth0"
date: 2007-04-27
forum: Installation &amp; Upgrades
---

### Post by fiestaforever on 2007-04-27
Hi, 

I'm just giving Xubuntu another try on an old Thinkpad 600E (1999 vintage) where I wasn't too happpy with both Ubuntu and Xubuntu in the past. So far it looks better this time, but I ran into one first problem: 

After adding "acpi=force" to the kernel line in grub, my IBM 10/100bT PCMCIA NIC (= eth0) stopped working. After I removed the "acpi=force" option, it resumed working. 

I've been using the  "acpi=force" option with other distros before without problem. 

Any ideas?

TIA

---

### Post by fiestaforever on 2007-04-29
Meanwhile, I adopted the following addition to the kernel line from another thread:
```
acpi=force pci=noacpi pnpbios=off pci=usepirqmask
```
This seems to help. But I wonder what exactly it does. I assume that the "pci=noacpi" was the relevant part here. 

Could anyone here explain the other parts for me?

The thread I've taken it from dealt with sound problems. I cannot check the sound on this machine, as it doesn't work anyway (and hasn't worked for years, despite much effort in various OSs, even with correct drivers; I've given up on that a long time ago).

---

