---
title: "reinstalling Karmic broke compiz on Acer Aspire 1410"
date: 2009-10-07
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Ryan_Singer on 2009-10-07
Hi Everyone,

I was running Karmic with compiz running great, but I reformatted and reinstalled to get onto ext4, and now compiz doesn't work. Help!

--
Ryan

---

### Post by Ryan_Singer on 2009-10-07
ryan@Acer-1410:~$ ./compiz-check 

Gathering information about your system...

 Distribution:          Ubuntu 9.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Software Rasterizer in use

---

### Post by Ryan_Singer on 2009-10-07
ryan@Acer-1410:~$ compiz
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 

Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1366x768) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: present. 
Software rasterizer detected, abortingaborting and using fallback: /usr/bin/metacity

---

