---
title: "Jaunty UNR and Dropbox Fail"
date: 2009-04-15
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by jdeslip on 2009-04-15
So, I recently updated two of machines to Jaunty.  On the regular jaunty install, dropbox works great and starts when I log into gnome.  

On my eee, I installed jaunty UNR.  Dropbox does not start when I log in to gnome.  It starts only after I click on home (or another folder).  I think this is because dropbox is started with nautilus.  Apparently nautilus is not started at gnome login in UNR as it is in ordinary jaunty.  I assume this is because of the lack of desktop.

Am I wrong about nautilus not being started in UNR?  Does anyone know how to tell UNR to load nautilus at startup the same way it is in ordinary ubuntu?  (adding to sessions doesn't really work)

---

### Post by jdeslip on 2009-04-16
Shameless Bump

---

### Post by Mud.Knee.Havoc on 2009-04-16
The new Dropbox package for Jaunty was just released (less than an hour ago! it's still warm!), so you might have more luck installing it.  

[https://www.getdropbox.com/downloading?os=lnx](https://www.getdropbox.com/downloading?os=lnx)

Here's the [forum post]("http://forums.getdropbox.com/topic.php?id=8470&replies=12#post-53870") announcing it.

EDIT: I should explain that Dropbox wouldn't work properly on Jaunty without a slight hack until this release.

---

### Post by jdeslip on 2009-04-17
Yep.  It is fixed with the new 0.6 package.  Thanks.

---

