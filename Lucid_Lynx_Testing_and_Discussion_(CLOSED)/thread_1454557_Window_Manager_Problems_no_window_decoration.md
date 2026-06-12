---
title: "Window Manager Problems: no window decoration"
date: 2010-04-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by skitching on 2010-04-14
I did "sudo apt-get update; sudo apt-get upgrade" today, and lost all window decorations.

The desktop still renders fine (icons, panels, etc) but windows have no titlebar (no title, close/min/max buttons), no resize margins. Focus follows mouse (previously was click-to-focus). Clicking on a window does not bring it to the front; most-recently-started is always on front.

I've tried changing theme, and theme colour does change but all themes have the same window-decorations. So I presume the window manager is having problems. Rebooting does not help.

I'm running the normal Gnome desktop.

Any ideas?

---

### Post by svtdragon on 2010-04-14
No ideas on a fix, but I just want to ditto this.  As a side note, at the same time, my mouse cursor turned from a pointer to an X, and my Chromium build doesn't allow me to enter text into the search/address bar.  I can load pages just fine by clicking, and I can type just fine into terminals or text boxes within web pages.  Not sure if they're related or if it's a coincidence.

---

### Post by svtdragon on 2010-04-14
This post helped me out:  [http://ubuntuforums.org/showthread.php?t=1451709](http://ubuntuforums.org/showthread.php?t=1451709)

I found out that metacity had gotten uninstalled by my last dist-upgrade.  I know my compiz installation won't work since I'm using an incompatible multi-monitor setup, and my desktop was falling back on metacity, which just got removed.

---

### Post by skitching on 2010-04-14
Thanks svtdragon.

The cause was indeed me having yesterday done "apt-get dist-upgrade", which caused compiz-gnome to be uninstalled. I guess either the problem didn't become visible until I rebooted, or I just didn't notice until after doing a second update.

Running
[INDENT]dpkg -l compiz-*[/INDENT]
clearly showed
[INDENT]rc compiz-gnome[/INDENT]

IE that I had accidentally uninstalled it. Reinstalling it returned the window decorations to normal. 

Yes, making metacity manage the window-decorations rather than compiz (ie running metacity --restore) also works, but the compiz way is the Lucid default configuration AFAIK.

Ah well, this episode pushed me to learn how to use "screen", which has always been on my to-do list :-)

And interestingly, Firefox was starting with its titlebar off the top of the screen; needed to use alt-spacebar|move to fix that.

---

