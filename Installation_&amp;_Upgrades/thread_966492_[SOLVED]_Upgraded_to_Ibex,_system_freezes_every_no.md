---
title: "[SOLVED] Upgraded to Ibex, system freezes every now and then"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by GeoMX on 2008-11-01
Did and online upgrade, had some trouble with **one** package (libwvstreams) during upgrade but solved after it. Got a terminal message saying that upgrade had failed, and that it would try going back by using dpkg --configure -a, but a GUI message saying the upgrade had succeeded :confused:.

Anyway, I rebooted and everything seem updated, new kernel, new firefox home page ;), etc. But, when booting, the system does not respond to my commands:

What works
- Panel launcher for Gnome Terminal, Firefox, Nautilus, Close session and desktop switcher.

What does not:
- Panel launcher for Ubuntu menu (the menu does not appear), Force closing application launcher, Compiz Fusion icon menu, Wireless icon menu, Volume icon menu, Hour/Date icon.
- I can open a terminal using the panel launcher, but I can not access it, the cursor is the one that appears when dragging the windows, not the one that is ready for entering commands.
- Firefox opens, but I'm not able to enter text anywhere, address bar, page forms... I can't navigate pages since I'm not able to move the scrolling bars.

But, everything fixes if I press Ctrl + Alt + F1! Sometimes I would go to tty1, without logging in I press Ctrl + Alt + F7 and everything is working now. Some other times I press Ctrl + Alt + F1, system seems to go to tty1 but goes back to GDM (tty7) inmediately, and again, everything seems to work... for some minutes :(, after working for some time, the system "freezes" again :( (Ctrl + Alt + F1 and it gets running).

Anyone having the same problem? I'm just doubtful about the problems I had while upgrading, if it seems I'm the only one with this problem, I'll try a clean install. In the meantime, I'll try disabling Compiz-Fusion (already tried this one), running GDM from tty1, and any other thing I can think of.

Hope someone can help, thanks in advance (and sorry for my poor English) :).

---

### Post by GeoMX on 2008-11-02
I made a clean install and the problem remains :S.

Fortunately, I've found the cause: blacklisting the video module. I added **video** to /etc/modprobe.d/blacklist as a workaround for the brightness keys problem ([https://bugs.launchpad.net/dell/+bug/226981/comments/3):](https://bugs.launchpad.net/dell/+bug/226981/comments/3):) when adjusting brightness it would change several steps at once. And now I've found that adjusting brightness causes the "freezes" I've been experiencing, all of them solved by switching to another tty and then going back to tty7.

I've removed **video** from the blacklist and the "freeze" problem seems gone. However, the brightness keys one is back :(.

---

### Post by GeoMX on 2008-11-02
I'm marking post as solved (but now I need a "real" solution for the brightness keys problem). BTW, my machine is a Dell XPS M1330 lap :).

---

### Post by zackiv31 on 2008-11-06
I have the EXACT same problems as you, thankfully I'm not alone with this bizarre behavior.. unlike you I'm not as savvy (didn't even know there was a Ctrl + Alt + F1 command :) .... and my machine just froze up and that seemed to have worked... sweeeeeet


My only difference, I'm on a desktop and don't have any monitor settings... so what is the underlying cause of this?


EDIT:  Still can't run... this solution only works for a minute for me, and I'm Ctrl + Alt + F1/7 every minute....  xfce has no problems, so my problem must be within gnome right?

Geo, if you could let me hijack your thread and change the title to not solved.. lol... cause all my problems are the same, but without a solution.

---

### Post by GeoMX on 2008-11-08
Did you make a clean install or an online upgrade?

Yes, the Ctrl + Alt + FX fix it only for some minutes :s. The problem appeared when I updated from Hardy to Ibex (using the the update manager). I could not notice the cause of the problem, so I decided to make a clean install and only then I could find out that the freezes occurred when trying to adjust brightness.

(The post is not marked as solved now).

---

