---
title: "Dual Booting... (yes I know, but read this)"
date: 2009-12-22
forum: Installation &amp; Upgrades
---

### Post by connor4312 on 2009-12-22
Yes, I know, you'll all say "read the tutorials!". I have, and it's not working.

I started with a Ubuntu computer, made a new partition (35 GB) for XP (for the Windows programs I can't run on WINE). Unfortunately, as expected, that knocked off Ubuntu's GRUB menu. I got that restored, but now there is no option to boot in XP. I tried editing the GRUB menu, but it seems there is no file at /boot/grub/list.lst (or whatever that filename was), nor any other files in the boot directory that looked remotely like that. Help Please!

Thanks,
Connor

---

### Post by connor4312 on 2009-12-22
Nevermind, I figured out I just have to run sudo update-grub :)

---

### Post by darkod on 2009-12-22
Did you try running
sudo update-grub

If you have clean install of 9.10 that menu.lst does not exist because it uses grub2. You should have /boot/grub/grub.cfg but usually you do not edit it manually.
See if update-grub will help first, and then we'll see depending on that.

---

