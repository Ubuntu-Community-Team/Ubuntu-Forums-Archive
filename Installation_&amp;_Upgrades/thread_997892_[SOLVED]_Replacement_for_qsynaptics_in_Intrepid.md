---
title: "[SOLVED] Replacement for qsynaptics in Intrepid"
date: 2008-11-30
forum: Installation &amp; Upgrades
---

### Post by roger_1960 on 2008-11-30
Hi 

Have just reinstalled Intrepid to a laptop to find that qsynaptics has recently disappeared from the repos.  How ese can I disable the mousetap and scrolling function of the synaptics touchpad?

I think synclient may do it but cant find any clear instructions - the man page doesnt make sense to me!

---

### Post by gpenguin on 2008-12-01
I have the same issue.  It seems people are migrating to 'g'synaptics.

I just selected it in 'synaptic' the package manager and there didn't seem to be any additional dependencies.

Just installed it and had to launch it manually in XFCE.  At first test, nothing lauches on boot or login...so it does me no good.  You still need, it seems, syndaemon.

--GPenguin

---

### Post by gpenguin on 2008-12-01
Forget gsynaptics unless you want to configure your touchpad itself.  For enabling/disabling the touchpad while you type, use 'syndaemon'.  It should be installed already on 8.10.  I put it in my Applications -> Settings -> Settings Manager -> Autostarted Apps

I used:

  /usr/bin/syndaemon -i 1 -d

-i sets the time interval to 1 second, and -d backgrounds syndaemon.

Hope this helps.

--GPenguin

---

### Post by roger_1960 on 2008-12-02
Hi

I think I have found the answer here:

[https://wiki.ubuntu.com/X/Config/Input](https://wiki.ubuntu.com/X/Config/Input)

This would seem to allow proper configuration in 8.10  I'll try it when I've time.  I think I also saw that the absense of a GUI for synaptics configuration in 8.10 has been logged as a bug. 

Thanks for the syndaemon advice - this does work but completely disables the touchpad which isn't really what I was after.

---

