---
title: "Boot failure after Bios update - GRUB"
date: 2009-11-24
forum: Installation &amp; Upgrades
---

### Post by UlleG on 2009-11-24
Hi,

I have a dual boot system Ubuntu 9.10 and Win XP. Yesterday I updated the BIOS and restarted the system. Computer booted and instead of showing the Grub boot selection screen it just said wrong system stuff and insert or change to proper boot device.

Each OS is installed on a different Hard-drive. 

The question is now, can I simply reinstall GRUB using Ubuntu live CD? If yes, is there something I have to keep in mind doing so?

Thanks for any help in advance.

---

### Post by namok on 2009-11-24
[Check it out.]("http://ubuntuforums.org/showthread.php?t=1014708")

---

### Post by PRC09 on 2009-11-24
Maybe your boot order was changed because the bios update reset everything back to default.Try changing the boot order of your drives in bios and see if it works...

---

### Post by UlleG on 2009-11-24
Thanks,
I was so worried that I didn't check the setting in BIOS for the main hard drive. Now everything works.

---

