---
title: "Todays updates - I get lib/udev rules error"
date: 2010-02-19
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by VMC on 2010-02-19
Just after the latest updates, I last message I get says something along the lines of /lib/udev rules error. It flashes so fast I can't read it, and I have rebooted several times and manage to just get the tail end of the report.

The only rules that have been updated is "/lib/udev/rules.d/64-xorg-xkb.rules". It has time stamp of Feb19th.

If anyone else can read or have that error please let me know what its saying.

I have looked at every var/log I can think of with no indication of rules error.

I'm talking about the text messages you get by removing the "quiet" from linux string. This message comes in just after the *fsck* check.

---

### Post by Seren on 2010-02-19
IIRC you have to look at /var/log/daemon.log.

---

### Post by glasen on 2010-02-19
This should be the file "/lib/udev/rules.d/40-xserver-xorg-video-intel.rules". There is a typo in the file :
```
SUBSYSTEM=="drm", "ACTION=="change", ENV{ERROR}=="1", RUN+="/usr/share/apport/apport-gpu-error-intel.py"
```
Just delete the quote sign before the word "ACTION" and the error does not occur any longer.

---

### Post by timosha on 2010-02-19
I get this since today's update:

unknown key '"ACTION' in /lib/udev/rules.d/40-xserver-xorg-video-intel.rules:9

---

### Post by VMC on 2010-02-19
> **Seren said:**
> IIRC you have to look at /var/log/daemon.log.Thanks. I looked in that file before I remembered it said something along the lines of rules or udev. The error is there alright.

> **glasen said:**
> This should be the file "/lib/udev/rules.d/40-xserver-xorg-video-intel.rules". There is a typo in the file :
```
SUBSYSTEM=="drm", [COLOR="Red"]**"**[/COLOR]ACTION=="change", ENV{ERROR}=="1", RUN+="/usr/share/apport/apport-gpu-error-intel.py"
```
Just delete the quote sign before the word "ACTION" and the error does not occur any longer.Thanks.  Will do. BTW, were you able to read the message as it went by or did you see it in the daemon log file? I must have rebooted 10 times just to try and read the error message. I just caught a couple of words.

---

### Post by timosha on 2010-02-19
> **glasen said:**
> This should be the file "/lib/udev/rules.d/40-xserver-xorg-video-intel.rules". There is a typo in the file :
```
SUBSYSTEM=="drm", "ACTION=="change", ENV{ERROR}=="1", RUN+="/usr/share/apport/apport-gpu-error-intel.py"
```Just delete the quote sign before the word "ACTION" and the error does not occur any longer.

Cured ! Thanks a lot :p

---

### Post by glasen on 2010-02-19
> **VMC said:**
> Thanks.  Will do. BTW, were you able to read the message as it went by or did you see it in the daemon log file? I must have rebooted 10 times just to try and read the error message. I just caught a couple of words.
I had Plymouth de-installed till today, so i could read the error message during the boot process.

---

### Post by darkhole on 2010-02-21
Bug reported:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/525433](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/525433)

---

### Post by gomyhr on 2010-02-22
> **darkhole said:**
> Bug reported:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/525433](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/525433)
Bug resolved :-)

---

