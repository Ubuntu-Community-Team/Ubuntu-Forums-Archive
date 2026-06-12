---
title: "Grub1 not updating to the latest kernel that I've installed"
date: 2009-12-05
forum: Installation &amp; Upgrades
---

### Post by lethalfang on 2009-12-05
When I do 
sudo update-grub, I see
```
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.31-16-generic
Found kernel: /boot/vmlinuz-2.6.31-15-generic
Found kernel: /boot/vmlinuz-2.6.31-14-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

```

But the menu.lst still **only** shows kernel 2.6.31-14-generic!

Any ideas?

---

### Post by Ginsu543 on 2009-12-05
Just edit the menu.lst file yourself and change all references to 2.6.31-14-generic to 2.6.31-16-generic and reboot. Unlike the grub.cfg file in Grub 2, menu.lst in Grub-legacy was meant to be edited.

BTW, do you use the same handle in Cal forum sites like Bear Insider or Scout? If so, as a fellow Cal Bears fan, Go Bears!!!

---

### Post by lethalfang on 2009-12-05
> **Ginsu543 said:**
> 

BTW, do you use the same handle in Cal forum sites like Bear Insider or Scout? If so, as a fellow Cal Bears fan, Go Bears!!!

That's me!

---

### Post by lethalfang on 2009-12-06
Well, I just mv menu.list to something else and did update-grub again, and it worked.
Maybe there's something in the original menu.lst file that prevents it from being overwritten by upgrade-grub.

---

### Post by Ginsu543 on 2009-12-06
That'll do! :) 

Whenever I do a kernel update, I tell the installer to leave my grub alone and just edit the menu.lst myself. I've never used update-grub with grub-legacy.

---

