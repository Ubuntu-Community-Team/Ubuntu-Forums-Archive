---
title: "Missing system tray icons in new Ubuntu 14.04 installation"
date: 2015-09-11
forum: Installation &amp; Upgrades
---

### Post by timur-tabi on 2015-09-11
I have installed Ubuntu 14.04.  Everything works, except the system tray has no icons.  I've spent the better part of the day googling for answers and trying different things, but none of them worked.  I even created a new account from scratch, and that one still has the problem.

There must be a way to fix this without reinstalling everything.  The indicators are running:

```
$ ps aux | grep indicator
timur     6406  0.0  0.0 475792  7784 ?        Sl   11:49   0:00 /usr/lib/x86_64-linux-gnu/indicator-sound/indicator-sound-service
timur     6408  0.0  0.0 758476  5936 ?        Sl   11:49   0:00 /usr/lib/x86_64-linux-gnu/indicator-session/indicator-session-service
timur     6409  0.0  0.0 286748  5004 ?        Sl   11:49   0:00 /usr/lib/x86_64-linux-gnu/indicator-application/indicator-application-service
timur     6416  0.0  0.0 259324  2876 ?        Sl   11:49   0:00 /usr/lib/x86_64-linux-gnu/indicator-bluetooth/indicator-bluetooth-service
timur     6433  0.0  0.0 439932 14864 ?        Sl   11:49   0:00 /usr/lib/x86_64-linux-gnu/indicator-printers/indicator-printers-service
timur     6443  0.0  0.0 331292  3444 ?        Sl   11:49   0:00 /usr/lib/x86_64-linux-gnu/indicator-messages/indicator-messages-service
timur     6462  0.0  0.3 1663452 55260 ?       Sl   11:49   0:00 /usr/lib/x86_64-linux-gnu/indicator-datetime/indicator-datetime-service
timur     7027  0.0  0.0 449892 13048 ?        Sl   11:49   0:00 telepathy-indicator
timur    15109  0.0  0.0  11748   908 pts/2    S+   12:28   0:00 grep indicator
```

---

### Post by dino99 on 2015-09-12
i'm a gnome-shell user, and have installed the extension 'TrayIcon' to satisfy some apps and because it is what i prefer ):P
the extensions can be founs at extensions.gnome.org and/or with gnome-tweak

---

### Post by timur-tabi on 2015-09-14
I'm running Unity, not gnome-shell, so your advice doesn't help me.  My problem is specifically with Unity's Application and System Indicators.

Another symptom: If I go to Settings->Appearance->Behavior and set "Show the menus for a window" to "In the menu bar", I see the name of the application in the upper-left corner, but clicking on it does nothing, and I don't have any menus in the menu bar.  The menus are still in the application's windows.

---

### Post by timur-tabi on 2015-09-14
So it looks like I'm affected by bug [https://bugs.launchpad.net/ubuntu/+source/indicator-datetime/+bug/1253693](https://bugs.launchpad.net/ubuntu/+source/indicator-datetime/+bug/1253693)

---

### Post by v3.xx on 2015-09-14
And your able to use the work-a-round?

---

### Post by timur-tabi on 2015-09-14
Yes, I just start ./indicator-applet-appmenu manually from the command line, and everything works now.  Even the application menus appear in the menu bar.

What I don't understand is why the problem isn't reported by the OS.  All of these indicator applications are launched and running, and none of them notice that indicator-applet-appmenu isn't running!  When I go to the "Panel" setting in unity-tweak-tool, how come I don't see an error message there either?

---

### Post by v3.xx on 2015-09-14
I don't have any good answers.

Maybe v15.04 is the solution, that would get you on systemd. Next month 15.10 comes out.

Good luck

---

### Post by timur-tabi on 2015-09-14
Unfortunately, my system is managed by corporate IT, so I can't upgrade to 15.  They only recently offered 14 as an option.

---

