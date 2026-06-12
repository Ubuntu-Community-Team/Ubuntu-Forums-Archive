---
title: "Can't play music in gtkpod"
date: 2005-04-12
forum: Installation &amp; Upgrades
---

### Post by bigblop on 2005-04-12
My iPod is mounted (I can see the contents in Konqueror) and I can see all my music in gtkpod. But when I press play on one of the tracks I get the follwoing error:


user@ubuntu:~ $ gtkpod 
KThemeStyle cache seems corrupt!

/home/user/.gtk_qt_engine_rc:309: error: unexpected character `{', expected
character `}'

Gtk-WARNING **: Unable to locate loadable module in module_path:
"libgtkqt.so",

Gtk-WARNING **: Unable to locate loadable module in module_path:
"libgtkqt.so",
_IceTransOpen: Unable to Parse address 

Gtk-WARNING **: Unable to locate loadable module in module_path:
"libgtkqt.so",

Gtk-WARNING **: Unable to locate loadable module in module_path:
"libgtkqt.so",
libmikmod.so.2: cannot open shared object file: No such file or directory
Inconsistency detected by ld.so: ../sysdeps/generic/dl-tls.c: 72:
_dl_next_tls_modid: Assertion `result <= _rtld_local._dl_tls_max_dtv_idx'
failed!


I have tried to find this libgtkqt.so file/package in synaptic but without success. How do I play music in gtkpod??

---

