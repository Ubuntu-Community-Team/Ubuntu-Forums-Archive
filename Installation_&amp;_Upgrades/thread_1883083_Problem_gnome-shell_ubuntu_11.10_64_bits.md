---
title: "Problem gnome-shell ubuntu 11.10 64 bits"
date: 2011-11-18
forum: Installation &amp; Upgrades
---

### Post by ccarruitero on 2011-11-18
Hi, 

I Installed ubuntu 11.10 64 bits in lenovo z470, then I installed gnome-shell from apt-get. The install was succesfull. But when I log in don't have gnome-shell, only gnome-classic.

I tried reinstalling ubuntu and gnome-shell but I have the same problem.

I read maybe it's a problem from fallback mode and I will run this line to fix the problem.

gnome-shell --replace 

but I have this error

Xlib:  extension "GLX" missing on display ":0.0".

(gnome-shell:1782): Clutter-CRITICAL **: Unable to initialize Clutter: The OpenGL version could not be determined
Window manager error: Unable to initialize Clutter.

I read this probaly it's a error from the driver, because I don't have installed property drivers; but it's not my case. I have a property drivers installed.

I don't know what should do to fix the problem. I can appreciate guidance to solve this problem.

---

### Post by vishnu_sresht on 2011-12-08
I have the same problem on a Dell Latitude E4310 ! When I go to System Settings > Additional Drivers, it says that "No proprietary drivers are on use in this system."

---

### Post by raja.genupula on 2011-12-09
[http://ubuntuforums.org/showthread.php?t=1746571](http://ubuntuforums.org/showthread.php?t=1746571)

---

### Post by skillet-thief on 2011-12-18
I'm having the same problem, same error message. 

I have an ATI card. I tried getting rid of all the proprietary drivers (fglx stuff) and reinstalling the mesa glx libs, but none of that has helped.

---

