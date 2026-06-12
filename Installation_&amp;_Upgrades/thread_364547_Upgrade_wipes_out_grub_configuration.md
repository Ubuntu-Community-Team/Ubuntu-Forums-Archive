---
title: "Upgrade wipes out grub configuration?"
date: 2007-02-18
forum: Installation &amp; Upgrades
---

### Post by Zepalesque on 2007-02-18
I recently upgraded a number of components (I am runing Edgy) and noticed that my previous Grub configuration was wiped out. I had to manually update the config file to gain access to my other OS partitions from the boot menu.

Has anyone else seen this?

---

### Post by confused57 on 2007-02-18
> **Zepalesque said:**
> I recently upgraded a number of components (I am runing Edgy) and noticed that my previous Grub configuration was wiped out. I had to manually update the config file to gain access to my other OS partitions from the boot menu.

Has anyone else seen this?

You might want to read over this, especially the sections on "kopt" & "groot":
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

This is what update-grub uses when your grub menu.lst is updated...make sure to place "other" OS outside the section ###BEGIN AUTOMAGIC... & ###END DEBIAN...

---

