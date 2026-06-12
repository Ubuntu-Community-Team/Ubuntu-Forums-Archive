---
title: "Places Menu - Computer item not working"
date: 2009-06-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by scradock on 2009-06-22
I have noticed that Karmic still has an item Computer in the Places menu, but that clicking on it does not open Nautilus (as it used to) with a view showing mounted disks and File System. Nautilus briefly opens then closes.

To get to the File System, I now need to open Home Folder (or some other mounted location) from the Places menu, then select File System from the left-side menu in Nautilus.

This seems like an oversight - can I fix it myself? Or does this require work by developers?

---

### Post by descendent87 on 2009-06-22
Clicking "computer" in the places menu opens nautilus fine for me

---

### Post by ranch hand on 2009-06-23
I don't think I have ever clicked on that before, don't see the point of it.  I did check it to see if it was "live".  Works fine on this partition - 9.10A2-64.

I have A1-32, I have it up to date as of yesterday, on another HDD.  I will check it tommorow.

---

### Post by davideotape on 2009-06-23
I remember this bug appearing in either nautilus 2.27.1 or 2.27.2 . Have you made sure that you have installed all the latest updates?

---

### Post by chrisccoulson on 2009-06-23
This is a known gvfsd-computer crasher [1] triggered on some setups when devicekit-disks returns an empty vendor name for some drives. It's fixed in gvfs upstream, but I think it's waiting on some other packages before it can be included in Ubuntu

[1] - [http://bugzilla.gnome.org/show_bug.cgi?id=582772]("http://bugzilla.gnome.org/show_bug.cgi?id=582772")

---

### Post by ranch hand on 2009-06-24
I have just updated A1, it is not the same as A2 because it still uses the ole grub and maybe other small differences that I have not noticed.

The point, though, is that I do not have any problem with clicking on "computer and having it pop right up.

This is Karmic alpha1 updated and running 2.6.30.10.

---

