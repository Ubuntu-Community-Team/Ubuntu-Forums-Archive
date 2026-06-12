---
title: "Dual-Booting with Windows Vista and Ubuntu"
date: 2012-01-03
forum: Installation &amp; Upgrades
---

### Post by Black_Sirrah239 on 2012-01-03
I have Windows Vista and Ubuntu 11.04 dual-booting. The only bad thing is when I boot my computer it starts 'Windows Boot Managaer' and defaults to Windows Vista. Is there anyway I can make it default to Ubuntu, or even better, get it to start in GRUB instead of Windows boot manager.

Thanks for any help, 
Black_Sirrah239

---

### Post by darkod on 2012-01-03
Did you install proper dual boot or wubi inside windows?

With proper dual boot it would install grub2 on the MBR unless you told it otherwise during the install. The default is grub2 on the MBR.

If you still have windows bootloader you either have wubi, or you told grub2 to install on a partition, not the MBR.

---

### Post by Mark Phelps on 2012-01-03
If you installed using Wubi, do NOT attempt to reinstall GRUB -- that will not help and will only make things worse.

You should boot into Windows, enter "MSCONFIG" in the Start area, and when that appears, select the Startup Tab, and then change the default selection there.

---

