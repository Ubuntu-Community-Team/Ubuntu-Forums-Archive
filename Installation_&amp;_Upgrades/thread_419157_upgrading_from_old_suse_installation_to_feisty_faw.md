---
title: "upgrading from old suse installation to feisty fawn"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by daniel_ on 2007-04-22
I have a computer with windows xp and a copy of suse 9.1.  The suse installation is pretty old, so I just downloaded ubuntu 7.04 and I would like to delete the suse partition and install ubuntu. Would the bootloader still work for getting ubuntu to start then?

Or should I just delete the bootloader and the suse partition and replace that?

---

### Post by Adramelech on 2007-04-22
Install ubuntu over suse and let the ubuntu install the bootloader it will detect your xp partition

---

### Post by pepsi_max2k on 2007-04-22
yeah, installing grub from ubuntu should overwrite your old grub install, so long as it's installed to the same place (mbr usually).

---

### Post by louieb on 2007-04-22
When you get to the partitioning part of the install choose manual partitioning. If using the live cd just blow past the first screen and go on to the screen where you select your mount points. Just make your old suse / partition the new ubuntu / partition and check the format box. swap should filled the installer should reuse the old suse swap partition. You should be good to click next and go on with the install.

---

