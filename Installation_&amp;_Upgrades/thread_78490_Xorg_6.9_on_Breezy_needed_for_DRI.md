---
title: "Xorg 6.9 on Breezy needed for DRI"
date: 2005-10-18
forum: Installation &amp; Upgrades
---

### Post by assan on 2005-10-18
I have problems with setting DRI on Breezy on my laptop and Intel 855GM chipset. After long search with help of arnieboy and following his howto HOWTO: Enable DRI (3D support) on SAVAGE cards, I couldn't get DRI to work.
Similar problem was visible in many threats on ubuntuforums about Intel chipset 3D acceleration.
I received answer what is wrong from Roland Scheidegger dri-user list.
Problem is in Xorg in old version of ddx (2D) driver version 1.3 and should be 1.4.x and is 1.3.0

libGL error:
 i915 DRI driver expected DDX version 1-1.4.x but got version 1.3.0 

Strange thing is it should be ok in xorg 6.8.2 like in hoary and breezy. Solution is to install xorg 6.9.
There are few problems
1.Is it safe for system to install Xorg 6.9 from source?
2.Maybe is worth to wait when Xorg 6.9 or 7.0 it will be available in repositories maybe it will be in few next weeks
3.another solution is to downgrade DRI to match old version of ddx
4. come back to i810 driver shipped with breezy.

What is your suggestion? Answer 1, 2, 3 or 4? (I prefer 1 or 2)

---

### Post by daniels on 2005-10-19
Um, what did you do to your i810 driver?  I'd be downgrading to the driver in breezy, given that DRI works just fine on my i855GM with the stock drivers in breezy.

---

### Post by assan on 2005-10-19
First problem with i810 driver from breezy is not working second display (projector), needed for presentations.
Second problem is pretty low 3D acceleration. About 550 fps in glxgears, after DRI installation people reached 1000-1100 fps with i855GM.
Third issue many ubuntu users with i855GM had problems with DRI installation and I would like to solve this issue. (*pro publico bono*)
First problem is critical and third is very important.
Another aspect is gainingpoint of experience points in Linux and Ubuntu world.
I hope this reasons are good enough.

---

