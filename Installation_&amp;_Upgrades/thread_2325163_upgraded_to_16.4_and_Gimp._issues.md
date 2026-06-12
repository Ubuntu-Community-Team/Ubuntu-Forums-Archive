---
title: "upgraded to 16.4 and Gimp. issues"
date: 2016-05-19
forum: Installation &amp; Upgrades
---

### Post by papahonk2 on 2016-05-19
Hello,
after upgrading to 16.4 from 15.10 everything seems to run fine up till i needed to tinker in GIMP. I cant draw, or paint at all if i try to draw lines each one shows a blank layer in the side panel. a general google search found a gimpusers.com posting about a simular problem on a windows machine. and they said to
"I had this issue on every single image, even on new, blank ones.I solved the problem by uninstalling the software again and deleting every GIMP-related folder in C:\Users\(nameoftheuser)\
A fresh install then did the trick; go figure...thanks a bunch for your reply though.
I have gone into synaptic and opted to completely remove then reinstalled with no change. I will continue to search as time permits but i was wondering if anyone else had this issue. Thanks

---

### Post by vanadium on 2016-05-20
Try deleting your .gimp folder in your home folder, then restart gimp: it will then recreate the profile and thus restore default settings.

---

### Post by X-RED_Tech on 2016-05-20
> **vanadium said:**
> Try deleting your .gimp folder in your home folder, then restart gimp: it will then recreate the profile and thus restore default settings.

+1

---

