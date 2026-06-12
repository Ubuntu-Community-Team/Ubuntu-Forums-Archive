---
title: "Compiz broken?"
date: 2009-09-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by mudi on 2009-09-14
Compiz seems to be broken after dist-upgrading today.  I'm using an Acer Aspire One with an Intel GMA 945 (I think...) Here's what happens in a terminal:

```
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1024x600) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Couldn't find a perfect decorator match; trying all decorators
Found no decorator to start
```I did note the update removing several packages related to compiz when I ran the update.  Anyone know what happened?

---

### Post by BCurtisWX on 2009-09-14
not always is a dist-upgrade the correct way to do things.  You probably removed compiz on accident.  I imagine installing the compiz-* files back that were removed should solve it for the time being

---

### Post by mudi on 2009-09-14
Trying to install compiz again just gets me on a long string of broken packages... something here is broken.

EDIT: must have just caught my update at a bad time... I ran apt-get update again and now the compiz packages aren't broken anymore.

---

### Post by BCurtisWX on 2009-09-14
> **mudi said:**
> Trying to install compiz again just gets me on a long string of broken packages... something here is broken.

If noone else has any ideas I will post the output of the changes it wants to make to my system when I get home.  Maybe you can downgrade the packages updated for the time being.

---

### Post by mudi on 2009-09-14
Thanks, but apt-get update then reinstalling compiz  fixed it... must have just had bad luck on my timing with the repos!

---

### Post by philinux on 2009-09-14
Yes you did.

---

### Post by Tibuda on 2009-09-14
The update manager wished to uninstall compiz here too. I clicked Cancel, and try to update tomorrow.

---

