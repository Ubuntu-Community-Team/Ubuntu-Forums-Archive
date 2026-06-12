---
title: "Dual-Boot attempt - partition shrank ok, installed Ubuntu, Ubuntu doesn't boot"
date: 2005-09-21
forum: Installation &amp; Upgrades
---

### Post by starkruzr on 2005-09-21
The title says it all.  According to the advice I saw about dual-booting Linux and XP, I did not install GRUB in the MBR (installing it in the MBR hoses your XP install?) and instead installed it on /dev/hda2 (there is a recovery partition installed by Gateway that I want to preserve).  Now when I start up the machine, XP is fine but there is no option to start Ubuntu or XP.  Help?

---

### Post by SilentCacophony on 2005-09-21
That generally is not the way to go, unless you already had a boot selecter you wanted to keep instaed of grub.

Normally, you should install grub to the mbr, in which case it will scan other partitions for valid OSes, prompt you if it's correct, and write them all to your /boot/grub/menu.lst file (including windows.) When it boots, it'll present you with the list from the menu.lst file.

Anyway, look [here](http://ubuntuforums.org/showthread.php?t=24113) for info on how to restore grub to the mbr. I'm not sure if having written it to a partition prior will cause any problems or not, though.

---

### Post by starkruzr on 2005-09-23
[QUOTE=SilentCacophony]That generally is not the way to go, unless you already had a boot selecter you wanted to keep instaed of grub.

Normally, you should install grub to the mbr, in which case it will scan other partitions for valid OSes, prompt you if it's correct, and write them all to your /boot/grub/menu.lst file (including windows.) When it boots, it'll present you with the list from the menu.lst file.

Anyway, look [here](http://ubuntuforums.org/showthread.php?t=24113) for info on how to restore grub to the mbr. I'm not sure if having written it to a partition prior will cause any problems or not, though.[/QUOTE]

This helped.  Thanks :)

---

