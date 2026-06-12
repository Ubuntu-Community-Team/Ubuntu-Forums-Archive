---
title: "Jaunty Xubuntu and Compiz"
date: 2009-04-12
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by foxy123 on 2009-04-12
Has anyone tried to run Compiz Fusion with Jaunty Xubuntu and namely on XFCE 4.6? It does not run for me. If I run compiz as I did on intrepid (xfce 4.4) I've got this:

> ~$ compiz -fusion --replace
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz: 455: /usr/local/bin/compiz: not found
exec: 455: /usr/bin/xfwm: not found
.

---

