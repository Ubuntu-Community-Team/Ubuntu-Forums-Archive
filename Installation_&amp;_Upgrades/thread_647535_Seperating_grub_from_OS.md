---
title: "Seperating grub from OS"
date: 2007-12-22
forum: Installation &amp; Upgrades
---

### Post by Sir_Sid on 2007-12-22
I want to use my system to boot multiple distros, so I was wondering if there was  a way to keep grub from being overwritten everytime I install a new one. I probably will be removing distros and adding new ones every few months, but I dont want to render my system un-bootable because I killed grub by removing a distro. 
So..
How do you seperate grub from the individual distros. I want to be able to manually edit menu.lst and keep other distros from overwriting it.

---

### Post by kellemes on 2007-12-22
> **Sir_Sid said:**
> I want to use my system to boot multiple distros, so I was wondering if there was  a way to keep grub from being overwritten everytime I install a new one. I probably will be removing distros and adding new ones every few months, but I dont want to render my system un-bootable because I killed grub by removing a distro. 
So..
How do you seperate grub from the individual distros. I want to be able to manually edit menu.lst and keep other distros from overwriting it.

Assuming you use distro's that use Grub..
1- Let your new distro overwrite Grub when installing.
2- "fix" your last Grub-configuration (ergo.. point to previous menu.lst) using [SuperGrubDisk]("http://supergrub.forjamari.linex.org/").
3- Use "configfile=" in menu.lst to point to /boot/grub.menu.lst of the distro you just installed

This way you create a nested bootmenu.. You basically use one menu.lst as a base for your bootmenu (so you manage Grub from your prefered distro) and point to the different menu.lst's of the other installed distro's. This works pretty cool.

For details see..
[http://www.users.bigpond.net.au/hermanzone/p15.htm#1._Configfile]("http://www.users.bigpond.net.au/hermanzone/p15.htm#1._Configfile")

---

