---
title: "killall gnome-panel not restarting?"
date: 2010-03-04
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by tekstr1der on 2010-03-04
With all this theme switching business afoot, I am used to issuing

```
killall gnome-panel
```

to restart the panel and refresh stubborn (nm-applet) icons. However, I am finding the panel is no longer automatically restarted. Without the panel running, Alt-F2 is unavailable for use. I would then try

```
gnome-panel &
```

in hopes that it would run as a separate process from the terminal. However closing the terminal kills gnome-panel once again. How can I get this to start properly? Can I start it from a tty if I specify the display?

---

### Post by Atermoon on 2010-03-04
It happened to me for a bunch of days last week but now it restarts after killing it. I guess your system is up to date. If you're only doing it to refresh teh nm icon you can just right click and uncheck "enable networking", then enable it again (as long as you don't mind going offline for ~5 seconds).

---

### Post by tekstr1der on 2010-03-05
AFAIK, gnome-session is supposed to respawn gnome-panel if it is killed. Does anyone know if this is not happening intentionally by design or if this is a bug that need filing?

---

### Post by tekstr1der on 2010-03-08
Does anyone know how to restart gnome-panel properly in its own process these days without leaving the current session?

---

### Post by tekstr1der on 2010-03-08
Guess I'm not the only one experiencing this, hence the following bug:

[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/522047](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/522047)

Seeing that this issue is supposedly fixed, could anyone please verify that killing gnome-terminal does, in fact, trigger an automatic restart. I reinstalled the package, yet the problem persists. Perhaps the issue is local to me?

---

### Post by tekstr1der on 2010-03-09
Well this is a lonely thread, quickly drown out by opinions and polls about button positions and theme colors... Anyway, the fix for this problem:
> We don't set the restart style to SmRestartImmediately since the
migration to EggSMClient. This fixes that.

gnome-panel/gnome-panel.desktop.in.in | 1 +
1 files changed, 1 insertions(+), 0 deletions(-)
---
diff --git a/gnome-panel/gnome-panel.desktop.in.in
b/gnome-panel/gnome-panel.desktop.in.in
index 2ef1cd2..4ffce87 100644
--- a/gnome-panel/gnome-panel.desktop.in.in
+++ b/gnome-panel/gnome-panel.desktop.in.in
@@ -13,6 +13,7 @@ X-GNOME-Bugzilla-Version=@VERSION@
Categories=GNOME;GTK;Utility;Core;
OnlyShowIn=GNOME;
NoDisplay=true
+X-GNOME-AutoRestart=true
X-GNOME-Autostart-Phase=Panel
X-GNOME-Provides=panel
X-GNOME-Autostart-Notify=true
______________________

Is in the latest gnome-panel 2.29.91-0ubuntu2, but even after verifying that X-GNOME-AutoRestart=true was added to my gnome-panel.desktop file, the thing will simply not respawn after being killed.

If anyone here is testing Ubuntu 10.4 Lucid Lynx, could you please just issue:
```
killall gnome-panel
```
from a terminal and let me know if it restarts automatically? I would really appreciate knowing one way or the other so as to determine if the issue is local to my install. Also the bug has been marked fixed, so if it is not I need to get it reopened. 

Thanks.

---

### Post by vredley on 2010-03-09
I'm running Alpha 3, fully updated, and gnome-panel restarts automatically after being killed in a terminal. Hope that helps. :)

---

### Post by Sam on 2010-03-09
This should restart gnome-panel without using gnome-session respawn:
```
gnome-panel --replace &
```

---

### Post by tekstr1der on 2010-03-09
@vredley: Thank you. This lets me know the bug is fixed and the problem is on my machine. No surprise, it's been through a few dev cycles and several releases.

@Sam: Thanks! the --replace argument was what I was seeking!

---

### Post by VMC on 2010-03-09
> **tekstr1der said:**
> 

If anyone here is testing Ubuntu 10.4 Lucid Lynx, could you please just issue:
```
killall gnome-panel
```
from a terminal and let me know if it restarts automatically? I would really appreciate knowing one way or the other so as to determine if the issue is local to my install. Also the bug has been marked fixed, so if it is not I need to get it reopened. 

Thanks.

It did it several times using Alt+F2, then 'killall gnome-panel'.
It worked perfectly. I haven't had a need to kill the panel on purpose in a long time.

---

### Post by Didius Falco on 2010-03-09
I'm having the same issue on my PC. The ```
killall gnome-panel
``` command did kill the panel, but it never respawned.

I then used the ```
gnome-panel --replace &
```
command, and it did restart, but I have the following output in the terminal window:

```
** (gnome-panel:2248): DEBUG: Initialized Panel Applet Signaler.
** (gnome-panel:2248): DEBUG: Adding applet 1.
** (gnome-panel:2248): DEBUG: Adding applet 2.
** (gnome-panel:2248): DEBUG: Adding applet 3.
** (gnome-panel:2248): DEBUG: Adding applet 4.
** (gnome-panel:2248): DEBUG: Adding applet 5.
** (gnome-panel:2248): DEBUG: Adding applet 6.
** (gnome-panel:2248): DEBUG: Adding applet 7.
** (gnome-panel:2248): DEBUG: Adding applet 8.
** (gnome-panel:2248): DEBUG: Adding applet 9.
** (gnome-panel:2248): DEBUG: Adding applet 10.
** (gnome-panel:2248): DEBUG: Adding applet 11.



```

and it "hangs" there, never concluding. If I force the terminal window to close, the panel disappears again.

A reboot restores the panel, but the bug remains.

This just started after an update I did a couple of hours ago...

---

### Post by tekstr1der on 2010-03-09
> **Didius Falco said:**
> ...and it "hangs" there, never concluding.

Just hit <enter> and it will "conclude".

---

### Post by Didius Falco on 2010-03-09
> **tekstr1der said:**
> Just hit <enter> and it will "conclude".

Thanks!! Now to figure out why starting Synaptic kills the panel...which is how I got to this thread in the first place.

On Edit:

It's not Synaptic. I created a launcher on the desktop for Synaptic and it works perfectly with no panel problems. But nothing will launch from the menu, and trying to launch it kills the panel. There is a new thread here: [http://ubuntuforums.org/showthread.php?t=1425777](http://ubuntuforums.org/showthread.php?t=1425777) with a couple of others with the same problem.

---

### Post by vredley on 2010-03-09
After the latest update (and as reported elsewhere), the panel crashes when launching anything from the menu.

Still restarts automatically though. :p

---

