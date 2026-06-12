---
title: "gnome session manager - can't add new app to list"
date: 2008-09-08
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by rbmorse on 2008-09-08
After the 80+ updates I instllled this afternoon, I can no longer add an application to be run at startup through the gnome session manager (gnome-session). 

Invoking the add button brings up the dialog, but when I try to commit I get the error "the command entry cannot be empty" even though it is filled in and points to a valid executable. 

Additionally, attempting to edit an existing entry is unsuccessful. I can make changes but they are not "saved" or committed when I close the dialog window.

---

### Post by Nullack on 2008-09-08
Did you actually reboot to effect all changes?

---

### Post by autocrosser on 2008-09-09
That is a known bug---look at:  [http://ubuntuforums.org/showthread.php?t=906701](http://ubuntuforums.org/showthread.php?t=906701)

And add to the report if you have anything new......

---

### Post by Nullack on 2008-09-09
Well the old bug has a status of fixe committed in Ubuntu and upstream gnome has fixed it:

[https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/260910](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/260910)

---

### Post by autocrosser on 2008-09-09
True, but I have not seen the fix on my system--still having the same problem as before--think threads should be merged.......

---

