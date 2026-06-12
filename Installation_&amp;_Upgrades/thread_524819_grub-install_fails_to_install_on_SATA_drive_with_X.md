---
title: "grub-install fails to install on SATA drive with XP"
date: 2007-08-13
forum: Installation &amp; Upgrades
---

### Post by dkonrad on 2007-08-13
I'm trying to install Ubuntu on my Asus M2NPV-VM with a dual core Athlon 64. I have two SATA drives, and /dev/sda has windows XP installed and booting on /dev/sda2. /dev/sdb has nothing of interest on it. The cdrom is the only device on the parallel IDE buss.

My Linux partitions are:

/dev/sda1   /boot    ext3      16M
/dev/sda5   /           reiserfs    8G
/dev/sda6   /var      reiserfs    8G
/dev/sda7   /home   reiserfs   16G

The install goes well, until it is time to install Grub. I changed the target of grub-install from hd0 to sda. In both cases it failed.

[LIST=1]
[*]How can I get the error messages from grub (all I see is the generic message from grub-install)?
[*]What might the problem be?
[/LIST]

Thanks
Doug

---

### Post by dabl on 2007-08-13
> **dkonrad said:**
> 

I changed the target of grub-install from hd0 to sda. 



I don't think you want to do that -- just let it go to hd0 (in Grub-speak) which is the same location as sda (in new-libata-speak).  :)

---

### Post by dkonrad on 2007-08-13
I will try again with hd0 -- but I'm pretty sure I left it as hd0 the first time.

Doug

---

### Post by dkonrad on 2007-08-14
The problem turned out to be a /boot partition that was too small. It's all working like a dream now.

Thanks
Doug

---

