---
title: "Cannot change upper gnome panel!"
date: 2008-10-16
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by fjf on 2008-10-16
It is sort of nailed.  I cannot add applets, or delete them.  Right-clicking on top of an applet only says "launch", and right clicking anywhere does not offer to add new applets.  Anyone suffered this?.  Any fix?.  Disabling compiz does nothing.

---

### Post by fjf on 2008-10-16
I'll answer myself (can I thank myself too?).  I found the way here:  [http://ubuntuforums.org/showthread.php?t=949485&highlight=gnome+panel](http://ubuntuforums.org/showthread.php?t=949485&highlight=gnome+panel)

The magic line:  rm -rf .gnome .gnome2 .gconf .gconfd .metacity
  and reboot.  Back to default gnome.

---

### Post by marmuta on 2008-10-17
It's too late now, but next time try to uncheck 
/apps/panel/global/locked_down 
with gconf-editor.

---

### Post by fjf on 2008-10-17
Damn!.  Oh, well...

---

