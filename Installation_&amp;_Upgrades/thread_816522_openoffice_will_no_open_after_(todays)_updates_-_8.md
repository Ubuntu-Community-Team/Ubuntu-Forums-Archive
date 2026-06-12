---
title: "openoffice will no open after (todays) updates - 8.04"
date: 2008-06-02
forum: Installation &amp; Upgrades
---

### Post by rslrdx on 2008-06-02
Hi,

I have one box that was updated today, just the regular and rather seamless process, get notified and click the upgrade button.

system seems fine but openoffice will not open on that profile but I can see the splashscreen, it seems to load but nothing shows up on the screen. 

I created a second profile just to test it, and openoffice does run fine.

I've also tried to delete the .openoffice.org2 folder from that profile, logged out and logged back in, openoffice still will wont run. Even reinstalled the openoffice-core package, still no go... 

If I do sudo openoffice, it runs on that profile... 

What am I missing? I know it will be some little stupid thing that needs a reset at least :confused:

Thanks,
Rodrigo

---

### Post by rslrdx on 2008-06-03
anything?

---

### Post by tgrimley on 2008-06-03
Maybe check in ~/.xsession_errors for a clue?

Also are you using compiz? Try disabling that before you run OO

---

### Post by fochsenhirt on 2008-06-03
Does running it from a terminal provide any useful information?

Someone with symptoms exactly like yours [had success deleting a file OpenOffice creates]("http://ecartis.ausics.net/hypermail/slackware/07/10/9117.html") in /tmp.  You could try that:
> Have a look in /tmp -- there should be a file with a name similar to this:
OSL_PIPE_1000_SingleOfficeIPC_71ad46243bb91ed9f18b27623cc484d=

Remove it and all should be well. 

---

### Post by rslrdx on 2008-06-03
This might be a bug: 

[https://bugs.launchpad.net/ubuntu/+source/openoffice.org-amd64/+bug/236676](https://bugs.launchpad.net/ubuntu/+source/openoffice.org-amd64/+bug/236676)

And thanks for the replys, i will try the suggestions

Rodrigo.

PS: My box is also affected by this now and running it from terminal gives this: 

rodrigo@rodrigo-laptop:~$ Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0x7f528acc097c]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x15) [0x7f528acc0a15]
#2 /usr/lib/libX11.so.6 [0x7f528e98a323]
#3 /usr/lib/libX11.so.6(XCreateWindow+0x44) [0x7f528e981d54]
#4 /usr/lib/libgdk-x11-2.0.so.0(gdk_window_new+0x395) [0x7f528a86ac05]
#5 /usr/lib/libgtk-x11-2.0.so.0 [0x7f5285ef94c8]
#6 /usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x10f) [0x7f5289cfebcf]
#7 /usr/lib/libgobject-2.0.so.0 [0x7f5289d12386]
#8 /usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x875) [0x7f5289d140d5]
#9 /usr/lib/libgobject-2.0.so.0(g_signal_emit+0x83) [0x7f5289d14483]
#10 /usr/lib/libgtk-x11-2.0.so.0(gtk_widget_realize+0x77) [0x7f5285eea957]
#11 /usr/lib/openoffice/program/libvclplug_gtk680lx.so [0x7f52862a276d]
#12 /usr/lib/openoffice/program/libvclplug_gtk680lx.so [0x7f52862a316a]
#13 /usr/lib/openoffice/program/libvclplug_gtk680lx.so [0x7f52862a382b]
#14 /usr/lib/openoffice/program/libvclplug_gtk680lx.so [0x7f528627bf64]
#15 /usr/lib/openoffice/program/libvcl680lx.so [0x7f52922274ed]
#16 /usr/lib/openoffice/program/libvcl680lx.so [0x7f52921bc322]
#17 /usr/lib/openoffice/program/libvcl680lx.so(_ZN9TabDialogC2EP6WindowRK5ResId+0x5f) [0x7f52921f91cf]
#18 /usr/lib/openoffice/program/libsvx680lx.so [0x7f527eb4c084]
#19 /usr/lib/openoffice/program/libsvx680lx.so [0x7f527ed20db4]

---

### Post by calc on 2008-06-19
This looks like lp bug 185311

---

