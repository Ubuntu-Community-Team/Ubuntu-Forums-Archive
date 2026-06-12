---
title: "Desktop background can't change?"
date: 2010-03-30
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by sports fan Matt on 2010-03-30
It seems I cannot even access the "change desktop background" to add a new GTK theme, it will not activate after right clicking. Is anyone having this issue as well, and if not, what sort of bug should I file on launchpad?

---

### Post by sports fan Matt on 2010-03-30
Here is my error: (gnome-appearance-properties:2431): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed
Segmentation fault

---

### Post by sports fan Matt on 2010-03-30
I think I found the bug as well: [https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/518368](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/518368)

Gonna add myself to the list.

---

### Post by dinamic1 on 2010-03-30
same here

---

### Post by rickwood on 2010-03-30
You guys sure you're not running Windows 7 Starter Edition? :P Sorry, couldn't resist.

---

### Post by Crunchy the Headcrab on 2010-03-31
Can't use System > Preferences > Appearance either.

---

### Post by Ichtyandr on 2010-03-31
> **Crunchy the Headcrab said:**
> Can't use System > Preferences > Appearance either.

same problem here, simply does not start

---

### Post by MacUntu on 2010-03-31
Are you guys on 64-bit systems? I can't reproduce the segfault on my 32-bit installation.

---

### Post by Ichtyandr on 2010-03-31
yes on 64bit, when run from terminal gives me this:

(gnome-appearance-properties:1507): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed
Segmentation fault (core dumped)

---

### Post by pabc on 2010-04-01
Me too. Also on a 64 bit version.

---

### Post by robert shearer on 2010-04-01
32bit here.  However, yesterdays updates fixed it. :D

---

