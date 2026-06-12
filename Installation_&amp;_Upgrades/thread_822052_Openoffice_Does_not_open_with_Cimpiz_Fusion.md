---
title: "Openoffice Does not open with Cimpiz Fusion"
date: 2008-06-07
forum: Installation &amp; Upgrades
---

### Post by Banjogator on 2008-06-07
Hello Guru's, 
While Compiz and Destop Effects are running, I am unable to launch OpenOffice 2.4 beyond the startup splash screen. I cannot open new or existing OpenOffice documents. 

If I disable my NIVIDA Accelerated Graphics Driver (hardware support) and go back to Default Graphics 1024x768 then OpenOffice works fine.

Here is the error messages when I run ooffice in terminal with Desktop Effect Enabled:

banjogator@banjogator-desktop:~$ ooffice
banjogator@banjogator-desktop:~$ Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0x7f0e3914b97c]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x15) [0x7f0e3914ba15]
#2 /usr/lib/libX11.so.6 [0x7f0e3ce15323]
#3 /usr/lib/libX11.so.6(XCreateWindow+0x44) [0x7f0e3ce0cd54]
#4 /usr/lib/libgdk-x11-2.0.so.0(gdk_window_new+0x395) [0x7f0e38cf5c05]
#5 /usr/lib/libgtk-x11-2.0.so.0 [0x7f0e343844c8]
#6 /usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x10f) [0x7f0e38189bcf]
#7 /usr/lib/libgobject-2.0.so.0 [0x7f0e3819d386]
#8 /usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x875) [0x7f0e3819f0d5]
#9 /usr/lib/libgobject-2.0.so.0(g_signal_emit+0x83) [0x7f0e3819f483]
#10 /usr/lib/libgtk-x11-2.0.so.0(gtk_widget_realize+0x77) [0x7f0e34375957]
#11 /usr/lib/openoffice/program/libvclplug_gtk680lx.so [0x7f0e3472d76d]
#12 /usr/lib/openoffice/program/libvclplug_gtk680lx.so [0x7f0e3472e16a]
#13 /usr/lib/openoffice/program/libvclplug_gtk680lx.so [0x7f0e3472e82b]
#14 /usr/lib/openoffice/program/libvclplug_gtk680lx.so [0x7f0e34706f64]
#15 /usr/lib/openoffice/program/libvcl680lx.so [0x7f0e406b24ed]
#16 /usr/lib/openoffice/program/libvcl680lx.so [0x7f0e40647322]
#17 /usr/lib/openoffice/program/libvcl680lx.so(_ZN9TabDialogC2EP6WindowRK5ResId+0x5f) [0x7f0e406841cf]
#18 /usr/lib/openoffice/program/libsvx680lx.so [0x7f0e2d617084]
#19 /usr/lib/openoffice/program/libsvx680lx.so [0x7f0e2d7ebdb4]
banjogator@banjogator-desktop:~$

I would appreciate any help you could offer.

thanks,

BanjoGator:guitar:

---

### Post by Partyboi2 on 2008-06-08
There has been a bug report opened [[COLOR=Blue]here[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/openoffice.org-amd64/+bug/236676"). There is also a workaround mentioned and possible fix.

---

