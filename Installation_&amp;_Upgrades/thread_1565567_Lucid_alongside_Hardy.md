---
title: "Lucid alongside Hardy"
date: 2010-09-01
forum: Installation &amp; Upgrades
---

### Post by J&#7885;hn on 2010-09-01
Hi Everyone

I have a workstation running Hardy and would like to install Lucid alongside for multiboot purposes.

I have the following LVMs on the system:

/dev/mapper/pc-root
/dev/mapper/pc-home
/dev/mapper/pc-var
/dev/mapper/pc-other

I have now created

/dev/mapper/pc-lucid-root

But I notice my /boot partition is not LVM.

Before I trash the machine, am I safe to install Lucid into /dev/mapper/pc-lucid-root and mount the /boot partition without formatting?

Thanks for any advice

John

---

### Post by J&#7885;hn on 2010-09-06
Ok for anyone interested, the install is messy if you overwrite /boot. I've gone down the route of allowing Lucid to create it's own /boot partition within an LVM and left the original /boot partition for Hardy to use.

---

