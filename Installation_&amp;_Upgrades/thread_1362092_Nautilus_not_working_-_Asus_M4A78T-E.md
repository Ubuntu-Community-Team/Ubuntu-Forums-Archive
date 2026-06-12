---
title: "Nautilus not working - Asus M4A78T-E"
date: 2009-12-22
forum: Installation &amp; Upgrades
---

### Post by bcn17 on 2009-12-22
I have just built a computer and installed 9.10 amd64. There is one problem. I can't go to places and open a folder- It just thinks for a sec then nothing happens. If I plug in a usb drive it doesn't put a shortcut on the desktop either. However, I can navigate via firefox and 'save as' to the usb drive.

The specs:
Asus M4A78T-E 
AMD Phenom II 965
EVGA Geforce 9800
Crucial DDR3 12800

If I type into terminal:

```
nautilus
```

I get the output: 

(nautilus:2144): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Initializing nautilus-gdu extension

** (nautilus:2144): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:2144): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:2144): WARNING **: No marshaller for signature of signal 'ShareCreateError'

(nautilus:2144): GLib-GObject-CRITICAL **: g_signal_connect_object: assertion `c_handler != NULL' failed
Segmentation fault


Any help appreciated, I haven't found anyone else with the same problem.

---

### Post by BooSolo on 2010-01-31
I won't be of much help in fixing this but I can tell you you're not alone, this has just happened to me and I am at a loss on what to do. I'm a total baby when it comes to the Ubuntu OS so I don't really know how to go about fixing it.

---

### Post by afrodeity on 2010-02-05
Exact [same problem]("http://ubuntuforums.org/showthread.php?t=1399819"). If you create a second user account, you get nautilus back. But this not exactly the kind of workaround one wants. I need a fix.

---

### Post by bcn17 on 2010-02-07
Do you both have the same motherboard as me? Or any shared hardware? For me the problem is not always nautilus now. It varies from application to application.

---

### Post by afrodeity on 2010-02-07
Biostar P4M900 with Intel Celeron
GeForce 8400 GS graphics

Link to my problem [http://ubuntuforums.org/showthread.php?t=1399819](http://ubuntuforums.org/showthread.php?t=1399819)

---

