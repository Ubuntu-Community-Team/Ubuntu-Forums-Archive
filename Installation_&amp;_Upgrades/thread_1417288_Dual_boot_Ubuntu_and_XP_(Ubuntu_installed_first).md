---
title: "Dual boot Ubuntu and XP (Ubuntu installed first)"
date: 2010-02-27
forum: Installation &amp; Upgrades
---

### Post by apple_head on 2010-02-27
Hi

I'm going to be dual booting Ubuntu and XP and I need to make a backup of the GRUB boot loader, however whenever I type in the command:

```
sudo gedit /boot/grub/menu.lst
```

I just get a blank text document and cannot find it in the grub folder. It's like it doesn't even exist?

I know that XP will wipe GRUB after installation and that I'll have to use the Live CD to get it working again but if it doesn't display it then i'll be a bit stuffed...? :(

Does anyone have any suggestions on this?? O:)

Thanks :)

---

### Post by darkod on 2010-02-27
XP will overwrite just the part of grub that is on the hdd MBR, not your grub config files. But if you want to, you can still make a copy. From ubuntu 9.10 a new version of grub is used, called grub2. The main config file is not /boot/grub/menu.lst any more, it's /boot/grub/grub.cfg.

---

### Post by apple_head on 2010-02-27
Brilliant thats what I need to know :D

Thanks darkod :D

---

