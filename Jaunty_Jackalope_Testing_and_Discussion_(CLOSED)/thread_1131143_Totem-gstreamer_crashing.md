---
title: "Totem-gstreamer crashing"
date: 2009-04-20
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by aethralis on 2009-04-20
After upgrade to Jaunty totem-gstreamer started crashing right after starting to play any video (its not dependent on format). Installed totem-xine and got exactly the same message. The error message from the terminal is as follows.

```

tef@tef-laptop:~$ totem-gstreamer
/var/lib/python-support/python2.6/gdata/tlslite/utils/cryptomath.py:9: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import sha
The program 'totem-gstreamer' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 82 error_code 11 request_code 132 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

Even vlc player was unable to play videos (with default settings) - after I switched vlc preferences to X11 video output it started to play. Has anyone got some ideas as to what should I do? Tried to reinstall (from synaptic) python and totem etc. No help. Attached lspci if its possible to get any usful info from there.

Bizarre thing is firefox (youtube) videos are playing ok.

---

### Post by ssam on 2009-04-20
/var/log/Xorg.0.log might have something interesting.

looks like [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/359831](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/359831)

---

### Post by aethralis on 2009-04-21
Could not find any other solution and tried the live cd - there it worked. Reinstalled the system.

---

### Post by aethralis on 2009-04-22
Yes. Seems that this was dependent on xorg.conf (should have read the bug report pointed by ssam more carefully). Exactly the same thing started again after I connected tv to the machine (through s-video). The virtual setting (in SubSection "Display") in xorg.conf seemed to be the culprit. Ie I can't use the totem player with second screen. 

Seems to be also connected with this bug: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/354889](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/354889)

---

