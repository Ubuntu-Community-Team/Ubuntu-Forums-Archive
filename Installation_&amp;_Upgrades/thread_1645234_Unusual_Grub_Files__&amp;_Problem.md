---
title: "Unusual Grub Files  &amp; Problem"
date: 2010-12-14
forum: Installation &amp; Upgrades
---

### Post by Bobhuber on 2010-12-14
Since upgrading from 10.04 to 10.10 I have lost my custom splash screen, the higher resolution stated in the grub file and have gained several files new to me. In addition to grub (in /etc/default/grub) I have a grub.ucf-dist. In /etc/grub.d I now have additional files 
/etc/grub.d/00_header.dpkg-dist and /etc/grub.d/05_debian_theme.dpkg-dist.
When I update grub it seems to read the configuration files but does not effect the boot screen. ????

---

### Post by eloilop on 2010-12-14
Hi,
I have the same issue since upgrading from 10.04 to 10.10.
ad1

---

### Post by dino99 on 2010-12-14
run: system admin startup-manager

---

### Post by Bobhuber on 2010-12-14
> **dino99 said:**
> run: system admin startup-manager
That totally trashed the system and I had to restore 10.04 to even boot. 
Gonna play around with it some more.

---

