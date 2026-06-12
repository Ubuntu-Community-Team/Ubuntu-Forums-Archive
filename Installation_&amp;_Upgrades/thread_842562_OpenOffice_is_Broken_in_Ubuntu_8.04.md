---
title: "OpenOffice is Broken in Ubuntu 8.04"
date: 2008-06-27
forum: Installation &amp; Upgrades
---

### Post by xp_newbie on 2008-06-27
I Installed Ubuntu 8.04 on my brand new system. Everything works perfectly (including Compiz). However, when I try start:
> 
Applications > Office > OpenOffice.org Word Processor

I get the the OpenOffice.org 2.4 splash screen and then... Nothing! :(

I opened a terminal and typed 'openoffice' to try and see what's going on. Here is what I received:
```

 Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0x7f813c8be97c]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x15) [0x7f813c8bea15]
#2 /usr/lib/libX11.so.6 [0x7f8140588323]
#3 /usr/lib/libX11.so.6(XCreateWindow+0x44) [0x7f814057fd54]
#4 /usr/lib/libgdk-x11-2.0.so.0(gdk_window_new+0x395) [0x7f813c468c05]
#5 /usr/lib/libgtk-x11-2.0.so.0 [0x7f8137af74c8]
#6 /usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x10f) [0x7f813b8fcbcf]
#7 /usr/lib/libgobject-2.0.so.0 [0x7f813b910386]
#8 /usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x875) [0x7f813b9120d5]
#9 /usr/lib/libgobject-2.0.so.0(g_signal_emit+0x83) [0x7f813b912483]
#10 /usr/lib/libgtk-x11-2.0.so.0(gtk_widget_realize+0x77) [0x7f8137ae8957]
#11 /usr/lib/openoffice/program/libvclplug_gtk680lx.so [0x7f8137ea076d]
#12 /usr/lib/openoffice/program/libvclplug_gtk680lx.so [0x7f8137ea116a]
#13 /usr/lib/openoffice/program/libvclplug_gtk680lx.so [0x7f8137ea182b]
#14 /usr/lib/openoffice/program/libvclplug_gtk680lx.so [0x7f8137e79f64]
#15 /usr/lib/openoffice/program/libvcl680lx.so [0x7f8143e254ed]
#16 /usr/lib/openoffice/program/libvcl680lx.so [0x7f8143dba322]
#17 /usr/lib/openoffice/program/libvcl680lx.so(_ZN9TabDialogC2EP6WindowRK5ResId+
0x5f) [0x7f8143df71cf]
#18 /usr/lib/openoffice/program/libsvx680lx.so [0x7f8130da2084]
#19 /usr/lib/openoffice/program/libsvx680lx.so [0x7f8130f76db4]
```

Why am I receiving these errors? Isn't Synaptic Package Manager supposed to take care of everything?

How do I fix this?

Thanks,
Alex

---

### Post by xp_newbie on 2008-07-09
> **xp_newbie said:**
> Why am I receiving these errors? Isn't Synaptic Package Manager supposed to take care of everything?
And the answer is... because OpenOffice is Broken in Ubuntu 8.04 - or at least the latest update on the date I posted this broke OpenOffice...

> **xp_newbie said:**
> How do I fix this?
I just applied the latest batch of updates (60 of them) and now OpenOffice works!

Speaking of Ubuntu being ready for the average user...

---

### Post by mikewhatever on 2008-07-09
Is openoffice a valid command? What did it usually do? I've checked the menus, and the command to start Writer is <ooffice -writer %U>. Could that have been the problem?

---

### Post by xp_newbie on 2008-08-18
> **mikewhatever said:**
> Is openoffice a valid command? What did it usually do? I've checked the menus, and the command to start Writer is <ooffice -writer %U>. Could that have been the problem?

~> which openoffice
/usr/bin/openoffice

'openoffice' **is** a valid command. The fact that the update solved the problem demonstrates it. Also, the same problem existed from the GUI as well.  I used the command line for troubleshooting purposes only. I usually invoke OOo from the GUI menu.

---

