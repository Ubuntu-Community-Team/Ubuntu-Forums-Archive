---
title: "Installing Ubuntu alongside other distros"
date: 2006-11-28
forum: Installation &amp; Upgrades
---

### Post by jondi on 2006-11-28
Hi all, 
I'm currently running PCLOS & SUSE 10.1. I'm trying to install Ubuntu by installing GRUB on the root partition, so I can chainload from PCLOS's GRUB, but my Ubuntu installation fails when it come to installing GRUB. I presume that the MBR is the only place where it wants to go. I'm quite happy to let it do this as long as it recognises my other 2 OS, but I don't know if it will. I'd appreciate it if someone could give me some advice. 
Thanks.

---

### Post by taurus on 2006-11-28
Yes, it will and if somehow it doesn't pick up the other two Linux distros, then you just modify /boot/grub/menu.lst and add two entries in there for those OSes...

---

