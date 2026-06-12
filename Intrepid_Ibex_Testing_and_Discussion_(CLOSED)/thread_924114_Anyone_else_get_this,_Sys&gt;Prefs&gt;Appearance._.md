---
title: "Anyone else get this, Sys&gt;Prefs&gt;Appearance. Gnome-settings-daemon unable to start."
date: 2008-09-19
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by philinux on 2008-09-19
Every restart, I get large font sizes once logged in. clicking the appearance menu I get this error.

Then the appearance menu comes up. Usually the fonts reset to my preferences. Otherwise I bring up appearances menu and the fonts then reset.

---

### Post by phenest on 2008-09-19
Yep, and since ever in Intrepid. Not so bad now. But I can't help noticing that it's worse if I use the proprietary nVidia drivers.

---

### Post by Sand &amp; Mercury on 2008-09-19
It happened to me, but only once. Logging out and in again solved the problem and it hasn't happened since.

---

### Post by philinux on 2008-09-19
This happens for me every boot up.

---

### Post by dinxter on 2008-09-19
i get the same problem here every login. i need to start gnome-settings-daemon manually which fixes fonts and theme. i take it its a bug with that package or a gnome-session problem perhaps. is there a bug filed on this yet? i havent been paying attention :)

---

### Post by philinux on 2008-09-19
I've bugged it as I could not find one the same or any for Intrepid.
[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/272093](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/272093)

Please add any comments/

---

### Post by dinxter on 2008-09-19
looking at the xsession-errors i've now removed ~/.config/metacity settings and this seems to allow gnome-settings-daemon to start correctly and fix the fonts bug. i'm taking it a previous version of metacity left a problematic config file or something. does this work for anyone else?

---

### Post by dinxter on 2008-09-19
i stand corrected, it didnt last, possibly ' gnome-session[22691]: WARNING: Unable to find provider 'gnome-wm' of required component 'windowmanager' in .xsession-errors is the problem

---

### Post by philinux on 2008-09-19
Thanks for that and your added comment to the bug report.

---

### Post by autocrosser on 2008-09-19
I've had this on a ill-regular basis also..I'll goto Launchpad & confirm it.

---

### Post by dinxter on 2008-10-21
if anyones still having this problem seb bacher is looking for more information [https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/272093](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/272093)

---

### Post by philinux on 2008-10-21
This is fixed for me from the updates.

---

### Post by dinxter on 2008-10-22
heres a new one that prevents me starting the daemon altogether. anyone recognise this?

```
$gnome-settings-daemon --debug --no-daemon
// some DEBUG messages
[1224663643,000,xklavier.c:xkl_engine_start_listen/]     The backend does not require manual layout management - but it is provided by the application
ERROR: Caught a segmentation fault while loading plugin file:
/usr/lib/gstreamer-0.10/libgstlibvisual.so

Please either:
- remove it and restart.
- run with --gst-disable-segtrap and debug.
[1224663643,000,xklavier.c:xkl_engine_start_listen/]     The backend does not require manual layout management - but it is provided by the applicationCould not initialize GStreamer: Error re-scanning registry , child terminated by signal
```

bypassed it just now by moving the knackered library.

---

### Post by plun on 2008-10-22
> **dinxter said:**
> heres a new one that prevents me starting the daemon altogether. anyone recognise this?

bypassed it just now by moving the knackered library.


Yup, confirmed after this mornings update. Rather Nasty...#-o

Also gets a english keyboard when the daemon seg faults...:-k

Is it because of this one.. 
[https://lists.ubuntu.com/archives/intrepid-changes/2008-October/009191.html](https://lists.ubuntu.com/archives/intrepid-changes/2008-October/009191.html)


What do you mean with moving the knackered library

---

### Post by dinxter on 2008-10-22
" sudo mv /usr/lib/gstreamer-0.10/libgstlibvisual.so ~/Desktop/"

hardly elegant but it keeps things running for now

is there a bug open on this?

---

### Post by dinxter on 2008-10-22
actually, moving the library isnt required for me. removing libvisual-0.4-plugins solved it, it had no dependencies for me. possibly just a a temporary version mismatch, the plugins package is on 0.4.0.dfsg.1-2ubuntu3 whereas libvisual itself is 0.4.0-2.1ubuntu1.

---

### Post by plun on 2008-10-22
> **dinxter said:**
> " sudo mv /usr/lib/gstreamer-0.10/libgstlibvisual.so ~/Desktop/"

hardly elegant but it keeps things running for now

is there a bug open on this?

Not as I can see....  Can you please file one ?

[https://launchpad.net/ubuntu/+source/libvisual-plugins/+bugs](https://launchpad.net/ubuntu/+source/libvisual-plugins/+bugs)


Uninstall solves it nevertheless .... :)

---

### Post by dinxter on 2008-10-22
bug [here]("https://bugs.launchpad.net/ubuntu/+source/libvisual-plugins/+bug/287448")

---

### Post by plun on 2008-10-22
> **dinxter said:**
> bug [here]("https://bugs.launchpad.net/ubuntu/+source/libvisual-plugins/+bug/287448")

Thanks !

Confirmed bug.

---

