---
title: "vncserver font path issue"
date: 2012-05-02
forum: Installation &amp; Upgrades
---

### Post by Skaperen on 2012-05-02
I get the following error messages when trying to start a VNC based X server:

```
lorentz/root /root 92# vncserver -geometry 960x600 -depth 32
[B]Couldn't start Xtightvnc; trying default font path.
Please set correct fontPath in the vncserver script.
Couldn't start Xtightvnc process.[/B]

02/05/12 18:16:31 Xvnc version TightVNC-1.3.9
02/05/12 18:16:31 Copyright (C) 2000-2007 TightVNC Group
02/05/12 18:16:31 Copyright (C) 1999 AT&T Laboratories Cambridge
02/05/12 18:16:31 All Rights Reserved.
02/05/12 18:16:31 See http://www.tightvnc.com/ for information on TightVNC
02/05/12 18:16:31 Desktop name 'X' (lorentz:3)
02/05/12 18:16:31 Protocol versions supported: 3.3, 3.7, 3.8, 3.7t, 3.8t
02/05/12 18:16:31 Listening for VNC connections on TCP port 5903

Fatal server error:
Couldn't add screen
02/05/12 18:16:32 Xvnc version TightVNC-1.3.9
02/05/12 18:16:32 Copyright (C) 2000-2007 TightVNC Group
02/05/12 18:16:32 Copyright (C) 1999 AT&T Laboratories Cambridge
02/05/12 18:16:32 All Rights Reserved.
02/05/12 18:16:32 See http://www.tightvnc.com/ for information on TightVNC
02/05/12 18:16:32 Desktop name 'X' (lorentz:3)
02/05/12 18:16:32 Protocol versions supported: 3.3, 3.7, 3.8, 3.7t, 3.8t
02/05/12 18:16:32 Listening for VNC connections on TCP port 5903

Fatal server error:
Couldn't add screen

lorentz/root /root 93# 
```I looked in the script and found a list of 4 font paths.  They do exist.  Shouldn't the package depend on at least a minimum set of fonts to get started with?   What else is needed?  This is on Ubuntu 10.10 amd64.

---

