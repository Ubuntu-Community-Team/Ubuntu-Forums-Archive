---
title: "No more compiz"
date: 2008-06-21
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by LittleKoy on 2008-06-21
Until now, when I enabled desktop effects, my windows borders weren't showing, I couldn't move windows, ecc. so I needed to type this:

compiz --replace ccp & emerald --replace &

and everything went ok. But now it doesn't work anymore, and this appears:

Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Error: no 'core' plugin with ABI version '20080609' loaded

/usr/bin/compiz.real (ccp) - Error: InitObject failed
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'ccp'
/usr/bin/compiz.real (core) - Warn: Plugin 'core' already active

---

### Post by eeclark on 2008-06-21
What video driver are you using? Mine is not working because the fglrx driver is not available for 2.6.26-2-generic.

---

### Post by LittleKoy on 2008-06-22
> **eeclark said:**
> What video driver are you using? Mine is not working because the fglrx driver is not available for 2.6.26-2-generic.

The open ones... But I solved it, I needed to manually update compiz, because update-manager couldn't do it because of dependencies...

---

