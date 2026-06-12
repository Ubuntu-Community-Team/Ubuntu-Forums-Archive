---
title: "[SOLVED] Compiz Not Starting - Software Rasterizer Present"
date: 2008-10-27
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Izek on 2008-10-27
```
ubuntu@ubuntu:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1440x900) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: present. 
Software rasterizer detected, abortingaborting and using fallback: /usr/bin/metacity
```

How do I stop the rasterizer and use compiz? This is on ATI Radeon HD 3200 (Which previously had bugged support in Ubuntu 8.04, but has been since fixed in 8.10.)

---

