---
title: "Installer blocks to SiI 3112 attached disk despite Linux seeing drive OK"
date: 2009-11-27
forum: Installation &amp; Upgrades
---

### Post by andrewk7 on 2009-11-27
I have a problem installing Ubuntu 9.10 desktop to a SATA drive on my system. It uses a Silicon Image 3112A SATA controller and has a 80GB seagate drive attached. The drive shows up as /dev/sda and I can partition the drive using Linux fdisk from the 9.10 live CD, but it does not show up as a choice in the installer. How can I fix this?

Thanks

Andrew.

---

### Post by lemming465 on 2009-11-29
Does it show up as a choice in the installer if you run *sudo aptitude remove dmraid* from a terminal window first?  If so, are you using or has anyone ever used firmware/BIOS/fake RAID on this system, possibly on other disks (presumably with a windows OS)?

---

### Post by andrewk7 on 2009-11-29
> **lemming465 said:**
> Does it show up as a choice in the installer if you run *sudo aptitude remove dmraid* from a terminal window first?  If so, are you using or has anyone ever used firmware/BIOS/fake RAID on this system, possibly on other disks (presumably with a windows OS)?

I'll try that - thanks. openSUSE won the battle of the distros and has been the first to get installed on this old box - neither Ubuntu nor Fedora 12 worked. Fedora 12's installer burst into flames!

Still hate the brown colour scheme on Ubuntu and am mystified why it doesn't come with any decent colour schemes - grrrr!

Cheers

Andrew.

---

