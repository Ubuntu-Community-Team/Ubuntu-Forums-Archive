---
title: "Compiz broke"
date: 2008-11-28
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by phenest on 2008-11-28
After some updates today, I restarted to find AWN complaining of no compositing manager. I've been using Compiz, but now Desktop Effects won't start. So I've fallen back to Metacity.

I haven't looked into this yet, as I have to go to work now, but I have checked the nVidia driver is ok.

---

### Post by klim8 on 2008-11-28
You can still use awn with metacity. The steps required to enable compositing in metacity are:

1- press Alt-F2 to open the Run Application dialog and type gconf-editor.
Click Run.
2- Navigate to Apps->metacity->general.
3- Check the compositing_manager box, and Metacity will immediately restart with compositing!

---

### Post by super.rad on 2008-11-28
or just type this in a terminal to enable it
```
 *gconftool-2 -s '/apps/metacity/general/compositing_manager' --type bool true
```**and this if you want to disable it again**```
* *gconftool-2 -s '/apps/metacity/general/compositing_manager' --type bool false
```*

---

### Post by phenest on 2008-11-28
Using Metacity is not my problem. Why would Compiz suddenly break?

---

### Post by phenest on 2008-11-28
More updates and Compiz is working again.

---

