---
title: "Xsession error log? Querie"
date: 2008-05-04
forum: Installation &amp; Upgrades
---

### Post by evilc on 2008-05-04
In Feisty & Gutsy ther was GTK+ errors which were never solved now in Hardy I get on startup this xsession error message:

```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_AU.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
SESSION_MANAGER=local/clive:/tmp/.ICE-unix/5774
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
Shutdown failed or nothing to shut down.
xrdb:  "*Label.background" on line 220 overrides entry on line 150
xrdb:  "*Text.background" on line 226 overrides entry on line 191
xrdb:  "*Label.foreground" on line 232 overrides entry on line 151
xrdb:  "*Text.foreground" on line 238 overrides entry on line 192
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0422 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1680x1050) to maximum 3D texture size (8192): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Initializing nautilus-share extension
seahorse nautilus module initialized
11

** (nautilus:5861): WARNING **: Unable to add monitor: Not supported
I/O warning : failed to load external entity "/home/clive/.compiz/session/default0"
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Starting gtk-window-decorator
/usr/bin/gtk-window-decorator: Could not acquire decoration manager selection on screen 0 display ":0.0"
  PID TTY          TIME CMD
 5840 ?        00:00:00 pulseaudio
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.
```Can someone tell me in simple terms what is going on, I really do not want to keep deleting this file everytime I start the computer as was suggested with the previous versions.

tia,

---

### Post by evilc on 2008-05-11
Bump

39 views and no replies, surely I am not the only one with this glitch/error.

---

### Post by evilc on 2008-05-11
OK now I'm receiving phantom replies, just had an email response from Ubuntu,

```
Dear evilc,

I_love_p_quarles has just replied to a thread you have subscribed to entitled - [ubuntu] Xsession error log? Querie - in the Installation & Upgrades forum of Ubuntu Forums.

This thread is located at:
[http://ubuntuforums.org/showthread.php?t=782362&goto=newpost](http://ubuntuforums.org/showthread.php?t=782362&goto=newpost)

Here is the message that has just been posted:
***************
It has to do with the file system - a well known bug.  Repair by typing:

Code:
---------
sudo mkfs.ext3
---------
And you should be good to go.
***************
```

Yet there is no post here??? What's going on....

---

### Post by bapoumba on 2008-05-11
> **evilc said:**
> OK now I'm receiving phantom replies, just had an email response from Ubuntu,

<snip>

Yet there is no post here??? What's going on....
You got the post in the mail, but is has been removed from the forums. This user was not in a very nice mood and posted several inappropriate advices using an inappropriate username. Sorry for the inconvenience :)

---

### Post by evilc on 2008-05-11
I thought something like that was going on after doing search.

---

### Post by evilc on 2008-05-18
bump  124 views still no fix for xsession error

---

