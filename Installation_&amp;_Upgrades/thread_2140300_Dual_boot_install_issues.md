---
title: "Dual boot install issues"
date: 2013-04-29
forum: Installation &amp; Upgrades
---

### Post by Brewmast3r on 2013-04-29
Hey guys,

I have been having some issues with trying to install Xubuntu on a separate hard drive. My main hard drive is a Corsiar Force GT with Windows 7 installed. The seconds drive that I want to install Xubuntu on is a Kingston SSD. When I run through the installer it doesn't even recognize that Windows is installed on the first SSD, just that all of its space is available. So I select "Do something else" and I tell Xubuntu to install on the Kingston SSD also installing the boot loader on the same disk. Everything installs fine, but when I reboot to boot off of disk, it doesn't find grub, even if I tell BIOS to force boot off the Kingston SSD. Any tips?

---

### Post by fantab on 2013-04-29
What computer are you using? what are its specs? Did those disks come with the machine? Was windows 7 pre-installed?
Is there RAID in the picture?

Post the output of [**BOOTINFO SCRIPT**]("http://bootinfoscript.sourceforge.net/")

---

