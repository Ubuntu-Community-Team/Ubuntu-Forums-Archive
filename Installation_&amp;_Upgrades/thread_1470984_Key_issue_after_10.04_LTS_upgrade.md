---
title: "Key issue after 10.04 LTS upgrade"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by ai649 on 2010-05-03
I used the Update Manager to upgrade last night and now when I log into my box using VNC whenever I hit the 's' key on my keyboard it pops up the shutdown menu.

The only way I can "type" the key is to copy/paste it from something else.

I'm using generic keyboard for 105-key Us with windows key, and can't find any shortcut keys setup for it.

Any ideas on where I should start looking at this?

---

### Post by ai649 on 2010-05-03
When I'm on the local machine, everything seems to work fine.  When I run vncviewer to localhost though, the s key still pops up the shutdown menu.

I'm running TightVNC viewer 1.3.9 and VNC4 server, according to their --help output.

---

### Post by ai649 on 2010-05-04
Ok, I tried tightvncserver and that made it worse.  I changed my window manager to fluxbox in my vncserver configuration and the problem goes away.

So something in the Gnome setup must be causing the problem, I just haven't found what it is yet.

---

### Post by pbwest on 2010-05-04
Same problem with Nomachine NX from my MacBook Pro. The "s" keys gives the shutdowm menu, the "m" key gives the Mail menu.

The last time I had a problem like this it was because of gnome-do. I don't remember the details, but I slved it by removing gnome-do from my Suse 11.2 system.

This is a showstopper fos me, as all of my work in Ubuntu is done through NX.

---

### Post by ai649 on 2010-05-04
That does sound like something along the right track, but the gnome-do package isn't installed on my system.  :(

---

### Post by pbwest on 2010-05-04
I seem to have fixed this by deleting the panel, re-establishing and re-populating it on the host machine. Sussequent nx connections have not displayed the problem.

---

### Post by johnburbridge on 2010-05-05
Same here and that worked like a charm! Thank you, pbwest.

How did you get the idea that the issue was the panel and not Xvnc? Brilliant.

---

### Post by csogilvie on 2010-05-07
I'm having exactly the same problem.

Could you please detail what steps you took to fix this issue?

---

### Post by pbwest on 2010-05-13
> **csogilvie said:**
> I'm having exactly the same problem.

Could you please detail what steps you took to fix this issue?

Sorry about the delay. I didn't have the thread subscribed.

My memory is a bit hazy (getting old) but I think this is what I did.

On the actual machine, on the top panel, right-click and select Delete this panel. You still have the lower panel.

On the lower panel, right click and select New panel. Position it at the top. Now right-click and Add to panel.

The most important one is Menu Bar A custom menu bar. That one has the main menu , Applications, Places, System. Add the Shutdown and Log out menus.

I don't know how to add the normal shutdown menu, which includes logout.

Some one else may be able to help out.

---

### Post by pbwest on 2010-05-13
Because the problems all related to actions in the panel.

---

