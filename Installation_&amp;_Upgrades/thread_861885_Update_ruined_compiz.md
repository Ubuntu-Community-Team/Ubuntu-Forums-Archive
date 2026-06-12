---
title: "Update ruined compiz"
date: 2008-07-17
forum: Installation &amp; Upgrades
---

### Post by doubad on 2008-07-17
So the Update Manager did it's daily thing yesterday as per usual.  The update required a restart and it somehow affected compiz.  My Cairo-dock is black right now, the Screenlets are half missing, and Compiz isn't working what-so-ever.  It doesn't matter if I alt-F2 and start Compiz because it works for a couple seconds while loading (I can see cairo-dock and screenlets go back to normal) but then compiz shuts right back off.  On the compiz fusion icon it still has compiz as my default windows manager, toying around with that does nothing.  Anyone have any suggestions? Has it happened to anyone else?

---

### Post by tuxxy on 2008-07-17
whats the output of 

```
compiz --replace
```

---

### Post by doubad on 2008-07-17
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:71c2 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1440x900) to maximum 3D texture size (4096): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
Segmentation fault

---

### Post by doubad on 2008-07-17
anyone?

---

### Post by doubad on 2008-07-17
:(

---

### Post by doubad on 2008-07-19
Yar har, time to reinstall Ubuntu.
Or maybe try Mint

---

