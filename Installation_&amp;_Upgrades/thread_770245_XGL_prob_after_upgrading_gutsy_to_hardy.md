---
title: "XGL prob after upgrading gutsy to hardy"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by ayampanggang on 2008-04-27
Hello there guys,
after upgrading to hardy from gutsy, i experienced a few problems:

1. GDM: When booting the system, i always get the "greeter application seems to be crashing" error. **This is a minor problem that i'll look into after the following problem**.

2. XGL: **This is what i'm trying to solve in this thread**. I set XGL based on [**_this tutorial_**](http://ubuntuforums.org/showthread.php?t=488385).
This is the startup script:
```

#!/bin/sh
Xgl :1 -fullscreen -ac -br -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec dbus-launch --exit-with-session gnome-session

```

The problem is, after XGL has been started, the display automatically switch to Mesa driver instead of fglrx one. This does not happen when XGL is not started. (e.g. failsafe gnome settings).

I use fglrx 8.4.76 driver (the newest one at this moment). I'm sure i installed it properly, since glxgears yields over 3000 fps, and glxinfo also yeilds "direct rendering: yes".

How can i fix this problem so that XGL will start properly?

Thank you very much.

---

### Post by tanguyr on 2008-04-27
Hello,

The good news is that the latest versions of the fglrx drivers that came with Hardy now support AIGLX, so you no longer need Xgl. I was able to switch by just turning AIGLX and compositing to "True" in my xorg.conf and then starting compiz. 

The bad news (more of a warning) is that i'm experiencing some X-related problems at the moment, so take the above with a grain of salt. I can't be sure that they are related to this, but just in case. Loads of people on the forums seems *reasonably* happy with the AIGLX approach (and it's not like we'll miss Xgl now is it?)

Regs,
/t

---

### Post by ayampanggang on 2008-04-27
apparently the switching this also happens as i simply log in into gnome. But this does not happen when i log in into failsafe gnome. I'll start a new thread since this topic is not relevant anyomre.

Thank you for your help!

---

### Post by ayampanggang on 2008-04-27
apparently the switching this also happens as i simply log in into gnome. But this does not happen when i log in into failsafe gnome. I'll start a new thread since this topic is not relevant anyomre.

Thank you for your help!

---

