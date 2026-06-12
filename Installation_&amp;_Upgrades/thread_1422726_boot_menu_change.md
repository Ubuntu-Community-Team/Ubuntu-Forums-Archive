---
title: "boot menu change"
date: 2010-03-05
forum: Installation &amp; Upgrades
---

### Post by worksofcraft on 2010-03-05
I installed 64 bit Karmic Koala on a new partition, keeping my existing 32 bit and windows drives intact.

On restarting grub just hung, so I swapped two hard drive cables and u came my new grub menu... all the different operating systems seem to boot OK :) 

However I want to change it so that my old working 32 bit Ubuntu (that still has all my apps and data installed) boots by default.

Problem is there is no /boot/grub/menu.lst for me to edit ??? [-(

So can anyone help let me know where does this new grub loader get it's boot menu from these days, and how can I edit it ?

---

### Post by worksofcraft on 2010-03-05
OK solved...

sudo apt-get install startupmanager


and run that

(note all lower-case)

---

