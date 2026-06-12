---
title: "xsession unable to launch after upgrade to ibex 8.10 kubuntu"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by lapichiflati on 2008-10-31
Howdy,

Just upgraded from 8.04.1 to 8.10 Kubuntu.  I was running KDE4 on 8.04.1 and when I updgraded everything went well just my x-server wont run anymore, booting into a black screen with a mouse cursor after the splash screen.  It gives me "Xsession: unable to launch ... falling back to default session.  Well, anyway you will see the log file for Xsession.  I tried dpkg-reconfigure on all the usual suspects, kdm, kubuntu-desktop, xorg and no luck.  Also checked permissions on most files and they seem to be fine.  Any one have any ideas how to get my machine back to GUI?

```

Xsession: X session started for lapichiflati at Fri Oct 31 09:35:01 EDT 2008
Xsession: unable to launch "" X session --- "" not found; falling back to 
default session.
/etc/X11/Xsession.d/40guidance-displayconfig_restore: line 11: /usr/bin/displayconfig-restore: No such file or directory
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
/usr/bin/xmodmap:  unable to open file '/usr/share/apps/kxkb/ubuntu.xmodmap' for reading
/usr/bin/xmodmap:  1 error encountered, aborting.
kwin(6139) KDecorationPlugins::loadPlugin: kwin : path  "/usr/lib/kde4/kwin3_ozone.so"  for  "kwin3_ozone"
kwin(6139) KToolInvocation::klauncher: klauncher not running... launching kdeinit
kdeinit4: preparing to launch /usr/lib/kde4/libexec/klauncher
kdeinit4: preparing to launch /usr/bin/kded4
kdeinit4: preparing to launch /usr/bin/kbuildsycoca4
kbuildsycoca4 running...
kdeinit4: preparing to launch /usr/lib/kde4/libexec/kconf_update
kdeinit4: preparing to launch /usr/bin/knotify4
kwin(6139): Couldn't start knotify from knotify4.desktop:  "KDEInit could not launch '/usr/bin/knotify4'." 

```

---

### Post by lapichiflati on 2008-10-31
Ok, found a bugreport, following the second to last post fixed my problem... YAY!

[https://bugs.launchpad.net/ubuntu/+source/kdebase-workspace/+bug/287488]("https://bugs.launchpad.net/ubuntu/+source/kdebase-workspace/+bug/287488")

---

### Post by emuman on 2008-10-31
How to solve the problem? KDM does not work for me, GDM can start KDE.

---

### Post by lapichiflati on 2008-11-04
I think GDM is probably the login manager for gnome and kdm the login manager for kde

---

