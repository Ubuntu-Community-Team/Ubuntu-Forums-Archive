---
title: "Upgrade to Intrepid Causes Computer Lockup on Reboot"
date: 2008-10-26
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Matthileo on 2008-10-26
I update from Hardy to Intrepid today (clean install, deleted hardy partition first) and now sometimes when I reboot the computer freezes right before it would normally power off, and the screen flickers with different blocks of random colors and lines.  It does this until I hard-shutdown.

Help?

EDIT
It seems that EVERY time i select restart the computer freezes at the end of the shutdown process, and the screen just flickers...

EDIT EDIT
It also seems that it's not just when I restart, but also when I shut down :(

I would really appriciate some help, to me this is a major bug.

---

### Post by Matthileo on 2008-10-27
**bump** for omfg, screens shouldn't blink different colors and get all flickery, and line-y...

---

### Post by simonjames on 2008-10-27
This seems related to my problem that I got when installing intrepid. When the installation asked to reboot, my computer rebooted but frooze before the DELL logo could even appear. I never got colours or anything but considering my problems happen only during reboot and shutdowns, it might be connected. Also when booting into windows XP and restarting actually gives me the same results....I think something broke a piece of hardware...

[https://bugs.launchpad.net/ubuntu/+bug/270754](https://bugs.launchpad.net/ubuntu/+bug/270754)

---

### Post by PinkFloyd102489 on 2008-10-27
My laptop hangs at the end of it's shutdown process also.

Inspiron 1720

---

### Post by blakamin on 2008-10-28
Mine flickers and hangs too.. never see splash screen on shutdown, just black screen with flickery white lines
Acer Aspire 4520 with nvidia 7000m. 
Never happened in hardy but has done so with every release of intrepid since I started at alpha 5.

---

### Post by Matthileo on 2008-10-28
Mine's not hardware related, since Vista boots and shutsdown fine and now that I've switched back to hardy it runs fine too..

I've got a Dell XPS m1530 with 2.5ghz core 2 duo processor and the nvidia 8600m gt graphics card, dual boot Ubuntu and Vista.

---

### Post by rex303 on 2008-10-28
same here, e6600 + p5b + 4gb ram + 4870, dual boot on 2 different hds with xp.

a black screen pops up when rebooting or turning off, but actually waiting a few minutes brings to a reboot/power off, but it still is an issue.

---

### Post by mkokotovich on 2008-10-28
My laptop hangs at the very end of any shutdown/reboot sequence as well.  If I leave it for 5 minutes or so, then "acpid exiting" appears, and it completes the shutdown process.  Can anyone else confirm this behavior?

I have looked through the logs a bit and can't find anything interesting.

Running updated 8.10.

---

### Post by idjit4 on 2008-10-29
> **mkokotovich said:**
> My laptop hangs at the very end of any shutdown/reboot sequence as well.  If I leave it for 5 minutes or so, then "acpid exiting" appears, and it completes the shutdown process.  Can anyone else confirm this behavior?

I have looked through the logs a bit and can't find anything interesting.

Running updated 8.10.

I have the same exact thing happen on my system.  I haven't been able to figure it out yet either.  So far your post is the only one I have found that mentions this behaviour.  I sure would like to know if anyone has solved this.

---

### Post by jpeddicord on 2008-10-29
It's something funky with X and/or Compiz. If you are using Compiz, try resetting your Compiz configuration:

```
gconftool-2 --recursive-unset /apps/compiz
```

Note that this will remove any custom settings you may have applied to desktop effects. If this solves the problem, gradually try enabling some other plugins until you are able to reproduce the problem, and disable the problem plugin.

If you are not using Compiz or another comp. manager, then, well, I'm not sure. :P

---

### Post by blakamin on 2008-10-29
> **jacobmp92 said:**
> It's something funky with X and/or Compiz. If you are using Compiz, try resetting your Compiz configuration:

```
gconftool-2 --recursive-unset /apps/compiz
```

Note that this will remove any custom settings you may have applied to desktop effects. If this solves the problem, gradually try enabling some other plugins until you are able to reproduce the problem, and disable the problem plugin.

If you are not using Compiz or another comp. manager, then, well, I'm not sure. :P

Even with compiz disabled it still crashed (haven't tried in the last couple of days to disable anything... it's a bit late)... Back at alpha 5 (or was it 6), I thought it was that or my nvidia driver, but nothing so far has made a difference. It has also caused permanent lines on my lcd... as you could imagine I'm a little bit unhappy. I have resorted to clicking "shutdown" and closing the lid until the HDD stops and the fan slows to a crawl, then open and hard-shutdown.

edit: interesting last syslog though... This is totally different from new but causes same prob. 
```

Oct 27 20:55:30 blakamin-laptop console-kit-daemon[5253]: GLib-GObject-WARNING: IA__g_object_get_valist: value location for `gchararray' passed as NULL 
Oct 27 20:55:30 blakamin-laptop init: tty5 main process (4604) killed by TERM signal
Oct 27 20:55:30 blakamin-laptop init: tty4 main process (4603) killed by TERM signal
Oct 27 20:55:30 blakamin-laptop init: tty2 main process (4607) killed by TERM signal
Oct 27 20:55:30 blakamin-laptop init: tty3 main process (4608) killed by TERM signal
Oct 27 20:55:30 blakamin-laptop init: tty6 main process (4609) killed by TERM signal
Oct 27 20:55:30 blakamin-laptop init: tty1 main process (5675) killed by TERM signal
Oct 27 20:55:33 blakamin-laptop x-session-manager[5701]: WARNING: Running '/usr/bin/gconftool-2 --shutdown' at logout returned an exit status of '15' 
Oct 27 20:55:34 blakamin-laptop console-kit-daemon[5253]: WARNING: Unable to activate console: No such device or address 
Oct 27 20:55:37 blakamin-laptop bonobo-activation-server (blakamin-6558): could not associate with desktop session: Failed to connect to socket /tmp/dbus-Pq2yipPJGk: Connection refused
```

Unfortunately I didn't save old ones after my update from hardy and before my fresh install of the RC.

---

### Post by Lstormy10 on 2008-10-29
I also have a problem with my desktop computer hanging at shut down. It just ends up with a black screen with a blinking white line at the top left that is where my cursor is. It is extremely annoying because I have to do a hard reset everytime I shut down.

---

### Post by davidsrsb on 2008-10-30
Don't hit reset, you have to wait several minutes and it will go off or unplug the network cable. This is a common problem with intrepid

---

### Post by hexion on 2008-10-30
Same problem here.
It freezes always when it tries to shutdown ALSA so I doubt it's related to compiz.

---

### Post by Matthileo on 2008-10-30
> **davidsrsb said:**
> Don't hit reset, you have to wait several minutes and it will go off or unplug the network cable. This is a common problem with intrepid

That doesn't seem like it should be a common problem in an RC, and especially not in the full release.

---

