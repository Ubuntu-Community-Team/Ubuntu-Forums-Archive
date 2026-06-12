---
title: "Imagewriter bug"
date: 2009-07-17
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by drfox on 2009-07-17
I've reported this to Launchpad.
Trying to execute the usb-imagewriter package:
From the GUI, I get nothing
From the CLI, I get this error:
gksudo imagewriter
Traceback (most recent call last): File "/usr/lib/imagewriter/imagewriter.py", line 21, in <module>
    import gtk
ImportError: No module named gtk

I tried installing glade and the gtk python dev packages, but that didn't work. I can't find a package called gtk, gtk-python or python.gtk

Anyone have a workaround?  Larry

---

