---
title: "Need Help Unity Compatibility Issue Please"
date: 2011-04-27
forum: Installation &amp; Upgrades
---

### Post by leeman101 on 2011-04-27
Hi,  With 11.04, my hardware apparently is not compatible with Unity..  I read that I can use gnome or Unity 2d.  I can get into 11.04 in low-graphics mode.  I was wondering how I can set gnome or unity 2d as the default.  It's a bummer, because I was actually looking forward to Unity.  By the way... I am on an HP Pavilion dv7-1245dx, and the graphics card is integrated ATI radeon HD 3200, uses shared memory.. don't know if that info makes a difference or not..  Any help is appreciated.. Thanks.

Lee

---

### Post by leeman101 on 2011-04-27
SOLVED.  Not that anyone responded....  But i logged into Ubuntu in failsafe graphics mode, then activated proprietary ATI driver, and then rebooted as normal, and all is well.  Unity is working and is working just fine so far as I can tell.  So if anyone else is having this issue with an ATI card, then just do as I did, and it will probably fix the issue.
You activate driver by going into system settings > Hardware > additional drivers.

---

### Post by DMJ on 2011-05-19
I have the same GPU. At first I got it to work with the OS driver, but now I get a purple screen at login. I tried both the ATI driver and OS driver. Both gave some artifacts in Unity. Especially when using Compiz shift switcher. 

There's a bigger issue with this GPU though. Open a terminal and enter "top." Do some heavy graphics stuff: move windows around, etc. You'll notice that over time the memory usage for xorg increases substantially. This is because there's a memory leak in the driver. I don't get this issue with the OS driver. This is a common problem with ATI GPUs.

---

