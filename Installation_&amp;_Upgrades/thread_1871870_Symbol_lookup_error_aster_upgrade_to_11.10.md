---
title: "Symbol lookup error aster upgrade to 11.10"
date: 2011-10-29
forum: Installation &amp; Upgrades
---

### Post by abeku on 2011-10-29
Hi All,

No program runs on my desktop any more after i upgraded Ubuntu 11.04 to 11.10. i het this error message "symbol lookup error : /usr/lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0: undefined symbol : g_datalist_get_data"

I have run update and upgrade from main server repositories  and local server as suggested on some sites, installed gtk devs etc, but still nothing works. i finally downloaded the DVD iso and did an upgrade from there as well but the error still persist.
 Am running a 64bit machine
Help please, am in a fix now, 

thanks

---

### Post by mrugiero on 2011-11-18
I'm having the same problem. I temporary fixed it by compiling glib, but that gave other problems, between them, gsettings stopped storing my settings, with the infamous "GLib-GIO-Message: Using the 'memory' GSettings backend.  Your settings will not be saved or shared with other applications." message.
If I remove my build and reinstall glib from repos, I get again the broke desktop (it has been at least two or three weeks like this).
Official glib version according to Synaptic is 2.30.0-0ubuntu4.

Also, I can't get debconf to notice I do have installed libgtk2-perl...

---

