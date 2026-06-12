---
title: "Ubuntu,multiple HDDs and wacky bios"
date: 2012-03-24
forum: Installation &amp; Upgrades
---

### Post by Linksi on 2012-03-24
Hi All! 

I have headless ubuntu server running from compact flash that is using IDE-port of motherboard (Abit AB9).

I got 5 SATA HDD's also in server. 

Problem is that AB9 got famous bios that sometimes messes up hard drive boot priority and that makes system un-bootable.

So, could I somehow install grub on every HDD and make it boot the compact flash adapter? Or anything else here that might help with this issue?

Its kinda annoying to go on and plugin VGA-card, get monitor, keyboard and go to bios change boot priority.

---

### Post by darkod on 2012-03-24
Nothing is stopping you to install grub2 to the MBR of all disks if you want. Just boot your ubuntu and in terminal do:

sudo grub-install /dev/sdX

using a,b,c,d instead of X for every hdd you have one by one.

---

### Post by Linksi on 2012-03-24
Ah, I did that and it seems to be working. Thanks!

---

