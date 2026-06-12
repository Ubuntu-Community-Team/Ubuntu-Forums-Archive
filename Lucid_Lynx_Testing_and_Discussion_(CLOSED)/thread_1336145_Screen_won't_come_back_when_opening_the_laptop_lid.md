---
title: "Screen won't come back when opening the laptop lid"
date: 2009-11-24
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by yelo3 on 2009-11-24
Hi, I have a dell laptop, and I have a problem when I close the lid.
The option is "blank screen", not "suspend".

When I open the lid the screen remains off, until I repetely hit ctrl-alt-f1, so the VT1 will light up the screen, then I can switch to XORG back, and I see a gnome-display-properties notification sying that it couldn't activate the default monitor settings.

in my xsession errors I can see those lines:
```
../../../libdrm/intel/intel_bufmgr_gem.c:893: Error setting memory domains 1 (00000040 00000000): Input/output error .
../../../libdrm/intel/intel_bufmgr_gem.c:893: Error setting memory domains 2 (00000040 00000000): Input/output error .

(gnome-display-properties:2504): Gtk-WARNING **: Ignoring the separator setting

(gnome-display-properties:2504): Gtk-WARNING **: No object called:

```

Do any of you have this problem?

---

### Post by jfernyhough on 2009-11-24
I think this is (surprise, surprise!) an issue with Intel graphics. I have exactly the same on my D520 (testing the Lucid kernel backport on Karmic).

Stuff like this tends to be fixed as the kernel gets updated - remember the Lucid kernel is based on the RCs of 2.6.32.

---

### Post by yelo3 on 2009-11-24
You might be right. Do you think it's worth to open a bug?

---

### Post by ranch hand on 2009-11-24
Always file a bug.  They have made it easy for you.

---

### Post by jfernyhough on 2009-11-24
2.6.32-5 is in the repos - is it any better?

---

### Post by jgbelacqua on 2009-11-24
You can check these threads for a couple of interim fixes (which worked for me):

[http://ohioloco.ubuntuforums.org/showthread.php?p=8378801#post8378801](http://ohioloco.ubuntuforums.org/showthread.php?p=8378801#post8378801)
[https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/49521](https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/49521)

---

### Post by t1m on 2010-01-11
Hi,

Quick suggestion.

Try pressing the blue function keys, i.e. Fn + F5 (or F7 or F8). I think they helped fix a similar problem I had with several Dells.

Hope it helps.

---

### Post by cdEWoozy on 2010-01-11
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/505271](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/505271)

---

### Post by yelo3 on 2010-01-12
Isuscribed to that bug. did you try the "vbetool dpms on" trick?

---

