---
title: "WARNING: gdm_slave_xioerror_handler: Fatal X error"
date: 2008-08-01
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by BC7333 on 2008-08-01
Very strange.. started today with the 26-5  

(did not update today and yesterday was fine)

system started going randomly crazy...cursor/windows all over the place.. tried to reboot.. went ok until login.. would not accept input and the cursor was blinking wildly with accompanying music of random beeping.

tried booting again after hard off and same.

unplugged the laptop and went back to -4 kernel for the moment.


```
Aug  1 14:32:34 brian-laptop gdm[9522]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Aug  1 14:32:36 brian-laptop console-kit-daemon[9370]: GLib-GObject-WARNING: instance with invalid (NULL) class pointer 
Aug  1 14:32:36 brian-laptop console-kit-daemon[9370]: GLib-GObject-CRITICAL: g_signal_emit_valist: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed 
Aug  1 14:32:36 brian-laptop console-kit-daemon[9370]: GLib-GObject-CRITICAL: g_object_unref: assertion `G_IS_OBJECT (object)' failed 
Aug  1 14:32:43 brian-laptop gdmgreeter[17237]: GdkPixbuf-CRITICAL: gdk_pixbuf_new_from_file_at_scale: assertion `width > 0 || width == -1' failed 
Aug  1 14:32:43 brian-laptop gdmgreeter[17237]: GLib-GObject-WARNING: invalid (NULL) pointer instance 
Aug  1 14:32:43 brian-laptop gdmgreeter[17237]: GLib-GObject-CRITICAL: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed 
Aug  1 14:32:43 brian-laptop gdmgreeter[17237]: GdkPixbuf-CRITICAL: gdk_pixbuf_new_from_file_at_scale: assertion `width > 0 || width == -1' failed 
Aug  1 14:32:43 brian-laptop gdmgreeter[17237]: GLib-GObject-WARNING: invalid (NULL) pointer instance 
Aug  1 14:32:43 brian-laptop gdmgreeter[17237]: GLib-GObject-CRITICAL: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed 
```

---

### Post by BC7333 on 2008-08-01
This just in off the press:

Doing update (although did not update yet.. 404 err's)'-

DKMS:

Version 2.0.20.2-0ubuntu1: 

  * If kernel headers are missing during a module build, report 
    this status properly in DKMS auto installation service. (LP: #247523)

just guessing.. but maybe related, at least partially.

---

