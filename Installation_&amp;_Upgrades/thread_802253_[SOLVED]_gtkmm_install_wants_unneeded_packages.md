---
title: "[SOLVED] gtkmm install wants unneeded packages"
date: 2008-05-21
forum: Installation &amp; Upgrades
---

### Post by Lichte on 2008-05-21
I'm trying to install all the gtk/gnome mm packages and it wants to pull in gcc 3.:confused:  I already have the gcc 4 stuff installed. How do I keep if from pulling in unneeded packages?  Thanks.

---

### Post by dstew on 2008-05-21
What package are you trying to install? If you have Hardy, the Gtk-- package for GTK+ 1.2 is libgtkmm-dev, and for GTK+ 2.4 is libgtkmm-2.4-dev. It is possible that one of these packages really depends on gcc3. If that is the case, you just need to go with it. You could try to uninstall gcc3 after you install your GTK--, but if the package really depends on gcc3, some functions will likely fail. Also, was your gcc4 installed using the package manager? If not, it is possible that some gcc files are missing, or in places other than those expected by the libgtk packages, and the packages only know to use gcc3 to fix it.

---

### Post by Lichte on 2008-05-21
I have the newest Ubuntu-Studio, 8.04.  I know that gcc-3 isn't a requirement for gtkmm/gnomemm/libgdamm ( or any C++ wrapper libs for gtk/gnome libs ), so I checked my gcc installation.  I found that g++ wasn't installed, so I installed the build-essential package and problem solved!  Thanks for pointing me in the right direction dstew :).

---

