---
title: "Dual boot Ubuntu/XP fails"
date: 2007-09-22
forum: Installation &amp; Upgrades
---

### Post by krimz on 2007-09-22
I'm trying to install Ubuntu with dual boot (XP) on my fakeraid. I have followed the fakeraid-howto and I'm able to tell the boatloader (GRUB) to start Ubuntu but after that it only shows the startup screen for Ubuntu with the progress-bar and absolutely nothing happens. The startup sequence just hangs there. 

I've created the following partitions:

/boot : isw_chchicfjbc_Volume02
/ : isw_chchicfjbc_Volume03
swap : isw_chchicfjbc_Volume05
/home : isw_chchicfjbc_Volume06

and made these changes in grub:

root (hd0,1)
kernel /.../isw_chchicfjbc_Volume03

etc... (I made all the changes that the fakeraid-howto told me to do)

Anyone have an inkling of where (or what) I might be doing wrong?

Grub starts up alright and I can start Xp without trouble but when I choose Ubuntu it just stops working, displaying the Ubuntu startup-screen.

Edit: I might add that the raid (raw) has the mapping isw_chchicfjbc_Volume0 (XP is isw_chchicfjbc_Volume01)

---

### Post by krimz on 2007-09-23
*bump*

anyone? :-?

---

