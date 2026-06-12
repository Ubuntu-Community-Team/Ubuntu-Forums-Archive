---
title: "Cant install Ubuntu wubi 11.04 on raid 0 machine? (please help)"
date: 2011-07-12
forum: Installation &amp; Upgrades
---

### Post by tfast500 on 2011-07-12
so i have installed wubi on my windows 7 system before but when i had a single drive

i just bought two 640gb black wd drives and put them into raid 0

i run wubi and it asks me to restart to finish install. i reboot and i choose to boot into ubuntu... ubuntu loads up the desktop and immediatly pops up an error "No root file system is defined please correct this from the partition menu"

i assume its not able to read my raid 0

is there a fix or a way i can correct this?

---

### Post by Rubi1200 on 2011-07-12
Hi and welcome to the forums :-)

Wubi installs to RAID are not officially supported. Although theoretically possible, we have seen few cases where it actually works.

In your situation, I suspect the RAID0 is the problem. However, please post the boot info script results so we can take a closer look (there is a link at the bottom of my post with instructions).

---

