---
title: "Moving files in XFCE"
date: 2009-04-17
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by hardawayd on 2009-04-17
Everytime i move a file to another location it makes a copy of it instead of just moving the file.  How do you disable this feature in XFCE?

---

### Post by stumbleUpon on 2009-04-17
How are you moving the file? Drag and drop...?

If so and if you are moving the file across two hard-disks or across a hard-disk and a USB drive, then it will copy the file rather than move it. If you want to move it, right click on the file and 'cut' and then right click on the place where you want to move the file and then finally 'paste' it.


Using the terminal, you can do

```
mv path-to-file/filename destination-path
```

to definitely move the file.

---

### Post by MaX on 2009-04-17
Try holding "shift" to force-move the file. Holding "ctrl" force copies a file

---

