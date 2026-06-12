---
title: "Desktop effects could not be enabled"
date: 2008-10-23
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by afz902k on 2008-10-23
Hello there. I have the same problem, when trying to enable Desktop Effects, I get the error message "Desktop effects could not be enabled".

I'm using Ubuntu 8.10 (and my system is 'up to date'), should I downgrade to 8.04?

Also, I'm using the Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller driver (which doesn't appear to be propietary because if I open System >> Administration >> Hardware Drivers, the list appears to be empty).

I've already commented some lines in the /usr/bin/compiz file in which my video card driver was blacklisted.

What else can I do to make it work?

This is the output the "compiz" command spews out in a terminal:
```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x960) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: present. 
Software rasterizer detected, aborting aborting and using fallback: /usr/bin/metacity 
```

---

### Post by overdrank on 2008-10-23
Moved to Intrepid :)

---

### Post by bear24rw on 2008-10-28
I have this same exact problem, when I go to add xserver-xgl it says:

xserver-xgl:

Package xserver-xgl has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list


I am using 8.10

---

### Post by wgrant on 2008-10-28
Xgl is obsolete, dead, and has been removed. You should use something more normal.

---

### Post by hyper7 on 2008-10-28
> **wgrant said:**
> Xgl is obsolete, dead, and has been removed. You should use something more normal.

I guess you don't have to be helpful to be a developer.

---

### Post by wgrant on 2008-10-29
> **hyper7 said:**
> I guess you don't have to be helpful to be a developer.

While perhaps true, I lacked time at that point to post a full solution to the original poster's solution. I thus decided to quickly point out that Xgl was a dead end, and a solution which should not be pursued.

---

### Post by Ocxic on 2008-10-29
"sudo dpkg-reconfigure xserver-xorg" fixed it for me

---

### Post by pbean on 2008-10-30
I'm just messing around with Intrepid from a Live USB stick right now and experience a similar problem.

Via the Resolution Settings I can either Mirror my two screens (12.1" Laptop/1280x800; 20" external/1680x1050) and when I do that the Desktop Effects work fine. However with Mirror I can only select a resolution as high as 1024x768. When I disable Mirror I get a dual screen display with both screens in the right resolution (which is really nice, because I never got that to work) but can't set up desktop effects. 

When dual screen is on 'compiz' complains:
```
Comparing resolution (2960x1050) to maximum 3D texture size (2048): Failed.
```

When I set the resolution of my laptop screen to Off 'compiz' complains as well:
```
Comparing resolution (1680x1050) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: present. 
Software rasterizer detected, abortingaborting and using fallback: /usr/bin/metacity 
```

I hope anyone can help. :) I'd love to use native resolutions *and* Desktop Effects.

---

