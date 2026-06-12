---
title: "Using KDE4.1, seeing 'gnome' corruption when DE animates"
date: 2008-10-14
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by LadFromWales85 on 2008-10-14
Hey all,
I'll start by saying I've got no idea what to search for to find an answer to this problem.  I've had a look round on here and on launchpad and have found nothing that fits!

Basically, when minimizing, maximizing, switching virtual desktop etc etc, I can see gnome in the background.  I can even see the recently changed wallpaper and all of the icons on my desktop, which is distracting as I don't have icons on my KDE desktop!

It used to be that I'd sometimes see partials of a recent window in the animation, but seeing gnome is just bizarre!  It gets worse and worse the longer X has been running, as the animations gradually slow down.

The Device section from my xorg.conf
```
Section "Device"
        Identifier  "ATI RADEON X1900"
        Driver      "radeon"
        Option      "AccelMethod"       "EXA"
EndSection

```

Could it be that an instance of gnome is running in the background?  I'm not seeing anything obvious in the running processes, use KDM, and have KDE set as default session.

I have KDE's desktop effects enabled.  I don't knowingly run any gnome applications, so I am at a loss as to what is causing the problem to know how to fix it!

Any ideas welcome!  Will paste the contents of any configs as required :)

---

