---
title: "Update from 9.04 to 9.10 beta"
date: 2009-10-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Yuryspb on 2009-10-12
Hello! I was updating ubuntu 9.04 to 9.10 beta, but my notebook switched off during installation. Installation was on the last step - cleaning temp files. Now Ubuntu 9.10 loads, but there is only top bar, and no desktop. Programs start, but there is black screen instead of the workspace. Desktop loads normally only in filesafe mode. How can I fix that? How to update to 9.10 again?
Notebook - Asus L5800c

---

### Post by prshah on 2009-10-12
> **Yuryspb said:**
> I was updating ubuntu 9.04 to 9.10 beta, but my notebook switched off during installation. 

Summary: Boot into recovery mode (from the GRUB menu) and give the command```
dpkg --configure -a
``` to have the interrupted upgrade complete.

More details from [here]("http://ubuntuforums.org/showpost.php?p=4872499&postcount=1")

You won't need Internet connectivity to complete the upgrade.

---

### Post by Yuryspb on 2009-10-12
Thank you for the advice. I ran grub recovery, dpkg had removed lots of packages, but it didn't solve the problem.
I switched off Visual effects and now everything works. 
How can I enable visual effects? In 9.04 everything worked fine =(

---

### Post by prshah on 2009-10-12
> **Yuryspb said:**
> 
I switched off Visual effects and now everything works. 
How can I enable visual effects? 

Well lets see where you are getting the problem; boot normally (ie without visual effects) then open a terminal (Applications-Accessories-Terminal) and give the command```
compiz --replace
``` Post back the output.

---

### Post by Yuryspb on 2009-10-12
yury@yury-laptop:~$ compiz --replace
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1400x1050) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!
yury@yury-laptop:~$

---

### Post by Yuryspb on 2009-10-13
any ideas?

---

