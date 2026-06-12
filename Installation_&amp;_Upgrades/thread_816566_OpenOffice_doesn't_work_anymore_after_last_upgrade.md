---
title: "OpenOffice doesn't work anymore after last upgrade"
date: 2008-06-02
forum: Installation &amp; Upgrades
---

### Post by Axx83 on 2008-06-02
I upgraded this afternoon and openoffice doesn't start anymore.
This is what it gives me when I try to run it:

```
myname@myname-desktop:~$ ooffice -writer
myname@myname-desktop:~$ Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0x7f61593b097c]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x15) [0x7f61593b0a15]
#2 /usr/lib/libX11.so.6 [0x7f615d07a323]
#3 /usr/lib/libX11.so.6(XCreateWindow+0x44) [0x7f615d071d54]
#4 /usr/lib/libgdk-x11-2.0.so.0(gdk_window_new+0x395) [0x7f6158f5ac05]
#5 /usr/lib/libgtk-x11-2.0.so.0 [0x7f61545e94c8]
#6 /usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x10f) [0x7f61583eebcf]
#7 /usr/lib/libgobject-2.0.so.0 [0x7f6158402386]
#8 /usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x875) [0x7f61584040d5]
#9 /usr/lib/libgobject-2.0.so.0(g_signal_emit+0x83) [0x7f6158404483]
#10 /usr/lib/libgtk-x11-2.0.so.0(gtk_widget_realize+0x77) [0x7f61545da957]
#11 /usr/lib/openoffice/program/libvclplug_gtk680lx.so [0x7f615499276d]
#12 /usr/lib/openoffice/program/libvclplug_gtk680lx.so [0x7f615499316a]
#13 /usr/lib/openoffice/program/libvclplug_gtk680lx.so [0x7f615499382b]
#14 /usr/lib/openoffice/program/libvclplug_gtk680lx.so [0x7f615496bf64]
#15 /usr/lib/openoffice/program/libvcl680lx.so [0x7f61609174ed]
#16 /usr/lib/openoffice/program/libvcl680lx.so [0x7f61608ac322]
#17 /usr/lib/openoffice/program/libvcl680lx.so(_ZN9TabDialogC2EP6WindowRK5ResId+0x5f) [0x7f61608e91cf]
#18 /usr/lib/openoffice/program/libsvx680lx.so [0x7f614c9a1084]
#19 /usr/lib/openoffice/program/libsvx680lx.so [0x7f614cb75db4]
```

Does anyone have the same problem ?

---

### Post by Partyboi2 on 2008-06-02
Looks like there has been a bug report filed [[COLOR=Blue]here[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/openoffice.org-amd64/+bug/236676"). There is also a workaround suggested in the mean time.

---

### Post by Axx83 on 2008-06-03
Yes if I do this:
> The problem disappears if I uninstall package:
openoffice.org-gtk
openoffice.org-gnome
the program opens correctly, with a non-gnome interface obviously, but I can live with that for the moment. Let's hope they'll fix it as soon as possible. Thanks for the link ;-)

---

