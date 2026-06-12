---
title: "How to connect hard disks with preinstalled Ubuntu and Windows?"
date: 2011-03-09
forum: Installation &amp; Upgrades
---

### Post by Marzata on 2011-03-09
How to connect two hard disk drives with already preinstalled Ubuntu and Windwos on them?

I have 2 separate hard disk drives. The first one is on the PC and it is running WinXP (or Vista). The second one was in another computer and has Ubuntu (10.04) on it. When I connect the Ubuntu hdd to the PC, additionally to the Windows hdd, then nothing happens. When I connect only the Ubuntu hdd to the PC, it boots normally, and later connect the Windows hdd, again nothing. I can not reinstall either one. So, how to connect them both? Thank you.

---

### Post by Dutch70 on 2011-03-09
Edit: if you absolutely can't re-install either one, you may want to wait for a 2nd opinion before doing this, but that's how I did it, just a few weeks ago.

When you have both plugged in, hit escape when your computer first comes on. Then you should be able to choose the hdd to log into. Choose the one with Ubuntu on it. Then when you get logged in to Ubuntu, run ***sudo update-grub*** in a terminal. That should allow grub to pick up the windows hdd and add it to the grub menu. 

Be careful!!!

---

### Post by Marzata on 2011-03-09
Thank you! This is a good idea to try out. Is it the same version of grub in 10.04 as in 10.10?

---

### Post by Dutch70 on 2011-03-09
> **Marzata said:**
> Thank you! This is a good idea to try out. Is it the same version of grub in 10.04 as in 10.10?

Yes, both use grub2.

---

