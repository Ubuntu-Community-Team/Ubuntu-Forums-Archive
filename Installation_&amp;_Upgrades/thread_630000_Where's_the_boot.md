---
title: "Where's the boot?"
date: 2007-12-02
forum: Installation &amp; Upgrades
---

### Post by astro4travel on 2007-12-02
Hi,
I just installed Ubuntu on my secondary drive on my machine. The first drive, or C. drive has Windows XP on it. When I go to boot Ubuntu is the first to take the stage. I tried to change my boot up order in bios by making the C: drive the first to boot. Instead the secondary drive in  which Ubuntu is installed still boots first. Is there a setting in Ubuntu that would correct this? Or what should I do? Thank you in advance! michael

---

### Post by acron1 on 2007-12-02
your computer is booting of the "master boot record" in your c drive.
You need to edit Grub in Ubuntu to make XP your 1st boot choice.
Good luck

---

### Post by logos34 on 2007-12-03
Like acron1 said, grub installed on the mbr of the C: windows drive, overwriting the windows bootloader.  It goes by default to the first Bios boot disk (or primary master) regardless of whether you installed ubuntu on a different drive.  So all you need to do is [change the default OS in /boot/grub/menu.lst]("http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc").  Or if there is no windows entry on the grub menu screen, [add one to menu.lst]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_Windows_entry_into_GRUB_menu").

---

