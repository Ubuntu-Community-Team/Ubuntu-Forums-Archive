---
title: "Feisty Upgrade - Logs into blank scren, then does nothing"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by RyanPower on 2007-04-21
After upgrading to Feisty from Edgy on my laptop (Dell Insiron 2500), after I type my username and pass the screen goes blank and I await the usual loading thing to show up and then to log in. But nothing shows up and it doesn't do anything.

I then pressed the power buttem to do a hard reboot and I gt a brief glimpse of a command line loading things and I see that it's stuck loading "NFS kernel daemon" and won't (or can't) load it.

(I'm posting this on Lynx from the recovery mode, so that wrks!)

---

### Post by Crosbie on 2007-04-21
Sounds similar to my initial problems.  Are you using custom graphics drivers (eg, ATI ones)?

I had to edit gdm.conf-custom to change my display (from 1 to 0, contrary to apparent recommendations) before I could get X working properly.  Previously I'd see the login screen for a few seconds then blank.  Autologin would continue in the background; I could hear the startup theme playing.

Sound like a possible fix?

---

### Post by roboguy on 2007-04-21
Hi,

I seem to be having the same problem on my Toshiba laptop. Can you give slightly more specific details of what you did to fix this issue?

Thanks,
Roboguy

---

### Post by roboguy on 2007-04-22
Just in case anyone else strikes this problem, I installed the restricted modules and enabled the nvidia driver and everything came right.

---

### Post by Crosbie on 2007-04-22
@ Roboguy: If you were talking to me, I just went through the Beryl install process [here]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL").  

The particular section that solved this problem was this bit:

> First change gdm.conf-custom:

$ sudo nano /etc/gdm/gdm.conf-custom

Go to the very bottom of the file and add:

```
0=Xgl
[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo
flexible=true
```

When you reboot or restart the graphical session, the Xgl server should be running. 

My existing gdm.conf-custom was using display 1, and had a note to the efffect that it had to for ati; but for some reason that had stopped working.

---

