---
title: "Firefox Permissions issues"
date: 2009-10-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by LavianoTS386 on 2009-10-15
After some recent upgrades I can't save anything from firefox to my hard drive. I keep getting messages about permissions not being right. Anybody know what's causing this?

---

### Post by emarkay on 2009-10-16
Can you be more specific?  Is the HDU a different volume?  Can you save other data to the disk, say from Gedit or OO? Is it the directory or the entire disk that you can't write to?

---

### Post by LavianoTS386 on 2009-10-16
Where i am trying to save to is on another volume, but i have no problem saving to this volume with any other program (nautilus, openoffice)

---

### Post by gdonwallace on 2009-10-16
The first thing I would check are the permissions of the directory on that volume that you are attempting to save to.  Also check the user / group of that directory to make sure that you are a member of the group that has access to the directory.

If all you are doing is try to write, then I would set the permissions to 666 (chmod 666 <directory name>).  Also, when you display the permissions, check the last bit of the permissions (rwxr-wr-t)  If the permissions have that "t" at the end, that will do some really funky stuff to users that attempt to write to the directory.  The prior chmod command will also fix that.

---

### Post by LavianoTS386 on 2009-10-17
selecting the "execute" check boxes seemed to have fixed this for me.

---

