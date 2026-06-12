---
title: "boot loader"
date: 2008-05-10
forum: Installation &amp; Upgrades
---

### Post by megablaise on 2008-05-10
When Installing, I can't decide where to install the boot loader. By default I have (hd0). Installing there the system boots always with Windows XP without giving me the option to choose.
I have the following option for installing the boot loader:

hd0
/dev/sdb ATAHDT7225DLAT80 232.9GB
/dev/sdb1 Microsoft Windows XP Proffesional
/dev/sdb6
/dev/sdb7

Can you please help!
Many thanks!

---

### Post by Pumalite on 2008-05-10
Install Grub to default (hd0). That will give you dual boot.

---

### Post by aswinms on 2008-05-10
> **megablaise said:**
> When Installing, I can't decide where to install the boot loader. By default I have (hd0). Installing there the system boots always with Windows XP without giving me the option to choose.
I have the following option for installing the boot loader:

hd0
/dev/sdb ATAHDT7225DLAT80 232.9GB
/dev/sdb1 Microsoft Windows XP Proffesional
/dev/sdb6
/dev/sdb7

Can you please help!
Many thanks!

I assume you installed Ubuntu and then XP? This method has been known to cause issues, I suggest you take the pain of backing up your data and format the entire hard disk, install XP first and then Ubuntu, this usually works flawlessly.

---

