---
title: "Firefox quits suddenly - no error messages"
date: 2008-09-12
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by phenest on 2008-09-12
Running Firefox from a terminal gives this error when it quits:
```
Segmentation fault (core dumped)

*** NSPlugin Viewer  *** ERROR: NPP_SetWindow() get args: Connection closed

(npviewer.bin:8813): Gtk-CRITICAL **: gtk_style_detach: assertion `style->attach_count > 0' failed

```

It's been doing this for a while.

I wasn't sure of which package to report it against.

---

### Post by asac on 2008-09-12
> **phenest said:**
> Running Firefox from a terminal gives this error when it quits:
```
Segmentation fault (core dumped)

*** NSPlugin Viewer  *** ERROR: NPP_SetWindow() get args: Connection closed

(npviewer.bin:8813): Gtk-CRITICAL **: gtk_style_detach: assertion `style->attach_count > 0' failed

```

It's been doing this for a while.

I wasn't sure of which package to report it against.

we have MASTER bug for that open: 216496

its most likely caused by a plugin (flash, totem etc.). if you could find out which plugin causes this and maybe can even provide a step by step instruciton how to do it, please provide that info in the bug. Thanks!

---

### Post by Slug71 on 2008-09-12
Firefox 3.0.2 just came through in Update Manager. I suggest you update and check what version of Flash youre using. You should get Flash 10 if you dont already have it and make sure you also have Xulrunner 1.9.0.2.

---

### Post by phenest on 2008-09-12
I've reported to that bug, that disabling flash seems to stop the crashing.

---

