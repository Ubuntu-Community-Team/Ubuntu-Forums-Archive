---
title: "Duel Monitor with gnome panel"
date: 2008-07-24
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Naddiseo on 2008-07-24
I'm not sure if this is due to my configuration, or something different with these new nvidia drivers, but I can't for the life of me figure out how to stop gnome-panel from spanning both my monitors. 

I've attached my xorg.conf for reference.
Anyone got a quick fix, or is this a bug?

Thanks.

---

### Post by RAOF on 2008-07-24
I think it's a bug (in the nvidia drivers, what fun!).  The twinview setup I used to have no longer works properly - indeed, gnome-panel spans both screens.

My solution: nouveau.  No 3d available, but dual head works (even *dynamic* dual-head, shock horror!), and it's very fast.

---

### Post by Naddiseo on 2008-07-24
I would try them, but I can't install it.
```

xserver-xorg-video-nouveau:
 Depends: linux-nouveau-modules  but it is not installable

```

---

### Post by RAOF on 2008-07-24
You need to install module-assistant and build the modlules, by running
```

sudo aptitude install drm-modules-source module-assistant
sudo module-assistant auto-install drm-modules
sudo aptitude install xserver-xorg-video-nouveau

```

---

### Post by Naddiseo on 2008-07-25
Thanks, sort of works. I regenerated my xorg.conf, and added the nouveau driver. The "Screen Resolution" applet in Preferences menu now detects both my monitors, but when I turn off "Cloned Output" and reposition the monitors, then "Apply," nothing happens. So, I'm stuck with cloned screens. Is there a nvidia-settings type program for this driver?

---

### Post by RAOF on 2008-07-27
You probably need to add a Virtual line to your xorg.conf to tell nouveau to allocate a large enough framebuffer for both screens (this is one of the stupidities of current X infrastructure/the current nouveau driver).  Section II.5. "Placing outputs in a virtual screen" from [this howto](http://wiki.debian.org/XStrikeForce/HowToRandR12) will help.

---

