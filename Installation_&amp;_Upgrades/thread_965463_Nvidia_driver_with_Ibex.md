---
title: "Nvidia driver with Ibex"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by darkhammer8108 on 2008-10-31
i just installed Ibex fresh and am trying to get my nvidia 7900gs to work. it wont configure properly no matter what i do though. first i tried going to 
```
System -> Administrator -> Hardware Drivers
```
first i installed the 177 driver. 
when i restarted it gives me one of several errors iv seen. the errors are either that it cant find the type1 module or when i comment it out it says that screens are found but not usable. 
i then tried uninstalling everything nvidia and reinstalling the nvidia-common program. then i tried to install the 173 driver. same thing happens.
if i manually install either of the drivers then run a nvidia-xconfig i get the same problems. also, if i try just adding the line
```
Driver "nvidia"
```
to the xorg configuration i get the same issues.

does anyone know how to setup this driver? my monitor is a dell 2007fp but i also hae a 1905fp that i intend to run in xinerama with the 2007fp. i am currently doing this in opensuse 11.0.

---

