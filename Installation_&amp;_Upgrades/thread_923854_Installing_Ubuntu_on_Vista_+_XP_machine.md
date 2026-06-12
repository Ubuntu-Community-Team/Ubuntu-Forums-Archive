---
title: "Installing Ubuntu on Vista + XP machine"
date: 2008-09-18
forum: Installation &amp; Upgrades
---

### Post by netiad on 2008-09-18
I currently have Windows XP and Vista installed on my computer (one hard drive).

As you already know you have to install Windows XP first then Vista.

So my question is if I install kubuntu will it recognize the two other OS's (Vista and XP) and make a prompt in grub so I can boot into them?

Or should I install the 3 OS's in a different order?

---

### Post by Pumalite on 2008-09-18
Go ahead and install after using Vista partitioner to allocate space. If need be; you can easily edit /boot/grub/menu.lst

---

### Post by RedPandaFox on 2008-09-18
Its not that hard to do, the grub that installs should automaticly install it. 
I do the same with XP-Vista-Ubuntu

---

### Post by netiad on 2008-09-19
i have about 5 partitions total. i set a side some space for kubuntu on one of the partitions.

but the installer doesn't seems to detect any of them.

i have two options:

use entire disk

or manual

under manual there is only /dev/sda with an unknown format

---

### Post by Pumalite on 2008-09-19
Post:
sudo fdisk -lu

---

