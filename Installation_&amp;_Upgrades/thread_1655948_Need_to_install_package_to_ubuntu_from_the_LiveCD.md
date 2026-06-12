---
title: "Need to install package to ubuntu from the LiveCD"
date: 2010-12-30
forum: Installation &amp; Upgrades
---

### Post by jplo on 2010-12-30
(HP G56 with an AMD Radeon graphics chip), I found that after installing the ATI Catalyst control centre (as jockey recommended), the ubuntu boot splash defaulted to the ubuntu-text theme. I set about uninstalling the driver, to see if it made ubuntu-logo come back. When this was done, I rebooted, and the system got as far as plymouth disappearing (which had returned to ubuntu-logo) and it hung. I can't even get to a tty terminal. This message comes from the livecd, and I wondered if there was some way of intstalling a package to an existing ubuntu partition by using the livecd. 

Thanks in advance, gerbilschool!

Update - running standard Ubuntu Maverick i386/32-bit

---

### Post by jplo on 2010-12-30
Never mind- I will mark this a solved, as I have now solved the problem. I tried to use ```
chroot /media/Ubuntu
``` but chroot doesn't seem to connect to the internet, or pass it through to programs, so ```
apt-get install fglrx
``` didn't work.

However, I then rebooted and chose recovery mode from the GRUB menu, and 'dropped to root shell prompt with networking'. I connected using an ethernet cable that I happened to have lying about, and was able apt-get to my heart's content. 

All's well that ends well! (I guess)

---

