---
title: "manual partitioning on reinstall?"
date: 2008-03-21
forum: Installation &amp; Upgrades
---

### Post by mahela007 on 2008-03-21
HI. 
could anyone provide me with a walk through for reinstalling linux on the same partition on which it is already on?

---

### Post by forestpixie on 2008-03-21
boot the cd - when you get to partitioning - pick manual

then select the original partitions - tick the box for format, edit partition and use the appropriate mount point

---

### Post by mahela007 on 2008-03-21
what exactly is a mount point? I dont know much about partitioning .
if i do this will i have to repair GRUB or make any changes to it?

---

### Post by forestpixie on 2008-03-21
when you reinstall - get to the partitioning part as I said - highlight the partition you intend to install on, edit partition - then you will get a drop down box to pick the mountpoint - choose /

then close that part and you'll be back at the list of partitions, assume you've not got a seperate /home , the swap partition will be dealt with automatically.

---

### Post by mahela007 on 2008-03-21
if I do that will anything happen to the GRUB boot loader?
I read somewhere that uninstalling ubuntu will cause the bootloader to freeze

---

### Post by forestpixie on 2008-03-21
Are you reinstalling or uninstalling there is obviously a difference. If you were uninstalling then yes you would need to deal with the bootloader - but if you're reinstalling you don't.

---

### Post by mahela007 on 2008-03-21
I'm reinstalling. Does that mean that i dont have to worry about the bootloader at all?

---

### Post by forestpixie on 2008-03-21
yes - it'll be reinstalled as well.

---

