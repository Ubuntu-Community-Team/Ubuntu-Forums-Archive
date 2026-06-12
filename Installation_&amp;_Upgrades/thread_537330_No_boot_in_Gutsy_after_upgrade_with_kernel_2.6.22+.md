---
title: "No boot in Gutsy after upgrade with kernel 2.6.22+"
date: 2007-08-28
forum: Installation &amp; Upgrades
---

### Post by topynate on 2007-08-28
**Sorry for the double: can an admin remove this please?**

I recently upgraded to Gutsy. On rebooting, I found in impossible to mount my hard drive(s)_ - details below. I used the old 2.6.20 kernel instead, and had no further problems.
However, today, having upgraded to the kernel 2.6.22-10-generic, X doesn't work, so I'm motivated to solve this problem :-)

When I turn on the 'nosplash' option in GRUB, the first failure message is:
mount: Mounting /dev/disk/by-uuid/eb522...842 on /root
failed: Device or resource busy.

There follow a few more lines, before I get dumped to a BusyBox prompt. The weird thing is, I checked /boot/grub/menu.lst, and there's no difference whatsoever between the old lines and the new lines, apart from the kernel name.
Does anyone have any clue? I'm typing this from Lynx, by the way, so apologies if it comes out looking messed up. Cheers.

---

### Post by Pumalite on 2007-08-28
sudo dpkg-reconfigure xserver-xorg

---

