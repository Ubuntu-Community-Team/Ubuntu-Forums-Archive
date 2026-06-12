---
title: "Pulseaudio capabilities with polkit-gnome-authorization (Jaunty)"
date: 2009-02-23
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by shakaran on 2009-02-23
Hi guys, my pulseaudio not working well, in terminal show:

```
$ pulseaudio
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
E: core-util.c: Failed to create secure directory: Permission denied

```

This seems a problem with authorization. If I grant permissions to pulseaudio for me user and also root (with polkit-gnome-authorization) , the same errors is shown (see image attached).

How to fix this problem? I have that start session with gnome failsafe (it is annoying!!)

---

