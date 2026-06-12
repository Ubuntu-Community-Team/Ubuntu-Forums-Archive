---
title: "cannot find grldr in all devices windows 7"
date: 2011-08-09
forum: Installation &amp; Upgrades
---

### Post by ekfsksk on 2011-08-09
i installed ubuntu today by installing Wubi and after downloading i rebooted computer and selected ubuntu but i got an error saying
'Try (hd0,0): FAT16: NO WUBILDR' and there was few more but i forgot and at the end it says
'Cannot find GRLDR in all device Press CTRL+ALT+DELETE to restart'

it used to work when i had vista... any solutions? thanks

---

### Post by garvinrick4 on 2011-08-09
Just go into Windows and in C: drive right next to Users is a folder named Ubuntu open it
and uninstall it. Or even can use Add and Remove programs in Windows.
There should have been a entry in BCD in Windows called wubildr to boot Ubuntu from.
You can open BCD and see. (Windows boot manager)
```
bcdedit
```
From a Windows command line. 
See if there is an entry: I guess really does not matter if not working just uninstall and reinstall. Not worth the hassle unless you are on a mission.

---

### Post by ekfsksk on 2011-08-09
> **garvinrick4 said:**
> Just go into Windows and in C: drive right next to Users is a folder named Ubuntu open it
and uninstall it. Or even can use Add and Remove programs in Windows.
There should have been a entry in BCD in Windows called wubildr to boot Ubuntu from.
You can open BCD and see. (Windows boot manager)
```
bcdedit
```
From a Windows command line. 
See if there is an entry: I guess really does not matter if not working just uninstall and reinstall. Not worth the hassle unless you are on a mission.

il see if it works

---

### Post by bcbc on 2011-08-09
That problem is due to wubildr.mbr not being able to find C:\wubildr - I wrote something on it [here]("http://ubuntu-with-wubi.blogspot.com/2011/01/wubildr-wubildrmbr-and-grldr.html"). Hope that helps.

---

