---
title: "Terminal only after upgrade to 11.10 Beta"
date: 2011-09-07
forum: Installation &amp; Upgrades
---

### Post by piston9 on 2011-09-07
Just more FYI for when the next person gets this.

I used the upgrade process to move from 11.04 to 11.10 Beta 1. After upgrade I could only get a terminal. A pretty terminal, but only a terminal.

After about 3 hours work, turns out that during upgrade it had asked which GDM I would like - I can't remember my choice. But I resolved in the end through terminal with 

**sudo dpkg-reconfigure lightdm**

And choosing lightdm as the display manager. Reboot and I am back in. Finding that command earlier would have saved me a few hours....

For info I am on a Dell D830 (D-830) latitude laptop with Intel 965 chipset. As of now everything else is still working, though am getting some probably expected gnome errors which aren't affecting life yet...

Hopefully helpful to someone!

Drewe

---

