---
title: "Wubi don't want to instal ubuntu via win7"
date: 2011-11-04
forum: Installation &amp; Upgrades
---

### Post by vampirich on 2011-11-04
I’m trying to install Ubuntu via wubi but there is no button “windows instalation” in the menu. I guess it has happened due to incorrect Ubuntu deinstallation at Win7. Therefore, wubi refers to the previous installation. What files or registry keys does the wubi checks before installation at win7?

---

### Post by bcbc on 2011-11-04
It doesn't check anything. Are you trying to run it from a USB because it won't offer the windows install option in that case.

---

### Post by vampirich on 2011-11-04
usb, dvd - same result
but there is menu item "windows instalation" when i use usb or dvd with kubuntu + wubi
wubi version on both distributives are equal

---

### Post by bcbc on 2011-11-04
Actually I wasn't entirely accurate. It checks the size of the ISO (which in the case of a USB corresponds to the partition size). It only offers to install inside windows if the size is within a predefined range: greater than 600MB and less than 900MB  (actually the range is in bytes so its > 572 and < 858MB)

So... check the size of the ISO you are installing from. It has to be the Desktop CD ISO and if it's on a USB the partition must be < 858MB.

If that works in Kubuntu... well that would surprise me since it's the same version of Wubi.exe running.

PS you can burn the CD ISO to a DVD and install it using Wubi - the size of the ISO doesn't change. It's just the USB where you need to worry about the partition size.

---

### Post by vampirich on 2011-11-04
i have ubuntu 11.10 dvd release.
i tried 
-use iso file in virtual cd program
-burn it to dvd
it was no result. Tomorrow i will try this dvd on another pc. that will explain me, reason in my win7, or in iso with ubuntu

---

### Post by bcbc on 2011-11-04
> **vampirich said:**
> i have ubuntu 11.10 dvd release.
i tried 
-use iso file in virtual cd program
-burn it to dvd
it was no result. Tomorrow i will try this dvd on another pc. that will explain me, reason in my win7, or in iso with ubuntu

You cannot install in windows with the ubuntu dvd iso. Only the desktop cd is supported.

---

