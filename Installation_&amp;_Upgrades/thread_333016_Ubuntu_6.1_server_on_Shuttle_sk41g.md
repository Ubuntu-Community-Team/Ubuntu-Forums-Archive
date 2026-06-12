---
title: "Ubuntu 6.1 server on Shuttle sk41g"
date: 2007-01-06
forum: Installation &amp; Upgrades
---

### Post by ckagy on 2007-01-06
Folks, I'm having some real trouble getting Ubuntu Server 6.1 installed on a Shuttle SK41G box I have.  The hardware is as follows:

CPU: Athlon 2100xp
RAM: 512M
Chipset: Nvidia KM266

I've got an otherwise empty 80G HD installed along with a CD R/W.

Based on a posting online here, [http://bloodgate.com/hacking/shuttle_linux.html](http://bloodgate.com/hacking/shuttle_linux.html) , I've enabled the USB keyboard and mouse support in the BIOS.

Based on info at the same site, I tried booting with "acpi=off noapic" generates errors as does using either of these two bootcodes by themselves (i.e. "acpi=off" alone and "noapic" alone).

Booting without either of these codes also fails.  I should clarify - without either of the bootcodes, the system boots and will go through the installation process as far as installing the base system (i.e it will format the drive, set the keyboard, etc) at which point it consistently errors out reading the CD.  The CD is good though, I've confirmed it on another machine.

I'm looking for suggestions on what to try next (other than scrapping the machine).

Thanks,
-Chris

---

