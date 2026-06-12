---
title: "Compiz Segfaulting on startup"
date: 2009-04-09
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by snowball1288 on 2009-04-09
Im running an HP Mini 1033CL netbook with intel 945 graphics.
It would appear after updating last night (or possibly early this morning) that compiz is segfaulting on startup.  As a result, I'm running metacity for the time being.

$ compiz --replace& shows this:

kavi@Jawa:~$ compiz --replace&
[1] 6542
kavi@Jawa:~$ Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1get fences failed: -1
param: 6, val: 0
Comparing resolution (1024x600) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: get fences failed: -1
param: 6, val: 0
present. 
Checking for Xgl: not present. 
Segmentation fault (core dumped)

Can anyone make heads or tails of whats happening here?  It seems that opening anything compiz-related fails as well (compiz-manager, ccsm, compiz-icon, etc).  Anyone else experiencing similar issues?


lspci:

00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

---

