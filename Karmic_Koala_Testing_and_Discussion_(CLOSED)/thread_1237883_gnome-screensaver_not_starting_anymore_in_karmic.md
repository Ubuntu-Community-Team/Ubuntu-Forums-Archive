---
title: "gnome-screensaver not starting anymore in karmic"
date: 2009-08-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by nIRV on 2009-08-11
Starting about a month ago, the gnome-screensaver has stopped starting after the idle period time set in gnome-screensaver preference window. The problem appears both on my laptop (dell + intel video) and workstation machine (asus motherboard + nvidia video).

Anybody else facing this issue? Workaround?

---

### Post by cariboo on 2009-08-11
I had the same problem, updates today fixed it.

---

### Post by wayne_cat on 2009-08-11
> **cariboo907 said:**
> I had the same problem, updates today fixed it.

I have just tested it with the latest updates. Does not work for me.

I have started gnome-screensaver with:

```
gnome-screensaver --no-daemon --debug
```If I run:

```
gnome-screensaver-command -a
```I can see a new line in the output and the screensaver appears. But the timer settings from gnome-screensaver-preferences still do not work here.

---

### Post by nhasian on 2009-08-11
I experienced the same thing.  I dont use a screen saver though, i just blank the screen.  as a workaround you can use:

```
xset dpms 600
```

this will turn your monitor of after 600 seconds (10 mins)

---

### Post by nIRV on 2009-08-11
Hrm interesting to see many are affected by this issue. Is there a launchpad bug filed for this?

---

### Post by Vaun on 2009-08-12
I believe this herein lies with gnome-power-manager.  My laptop's display will not sleep ever with g-p-m installed.  Uninstalled g-p-m and the display sleeps again on a consistent basis.  I will test the upstream master when I get some time as there is much work being done to it everyday.  Uninstallation is by far not an optimum solution, but I need my monitor to turn off before I need it to suspend, hibernate, etc.

---

### Post by tekstr1der on 2009-08-12
> **nIRV said:**
> Hrm interesting to see many are affected by this issue. Is there a launchpad bug filed for this?

[https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/397892](https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/397892)

It was originally filed against Xubuntu, but affects all flavors I assume.

---

### Post by taavikko on 2009-08-12
> **tekstr1der said:**
> [https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/397892](https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/397892)

It was originally filed against Xubuntu, but affects all flavors I assume.

Confirmed.

---

### Post by phenest on 2009-08-12
I wondered if this was a power management issue. I find my display dims as soon as I set the option in power management. If I put the brightness back to full, it will drop again when idle and will not return. Also, my screen goes blank when I'm using it (albeit mouse and not keyboard).

Could the screensaver issue be a part of this somehow?

---

