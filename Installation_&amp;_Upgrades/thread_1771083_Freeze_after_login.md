---
title: "Freeze after login"
date: 2011-05-30
forum: Installation &amp; Upgrades
---

### Post by quequotion on 2011-05-30
Since upgrading to 11.04, I encounter a system-wide hard freeze after login.
Even the mouse cursor animation freezes, and blind attempts to use the keyboard have proven ineffective.
Ocassinally the HDD led stays on as well.

I can log in to "Ubuntu (Sade Mode)" only.
By running ```
compiz --replace
``` I am able to open an use Unity in Safe Mode, but it looks and performs atrociously.

I have an AMD Athlon 64 x2 CPU and an nVidia GT 220 GPU.
I have seen lots of forum posts, a few bug reports, and some blogs about issues attributed to nVidia in Natty. I'm not convinced it's just an Nvidia problem after trying three versions of the driver.

Just to get a few questions out of the way:
1. My card is not blacklisted.
2. Unity claims my card is fully compatible.
3. Driver failure doesn't appear anywhere in my Xorg logs.
4. I already threw out my compiz configuration once, no change.
5. Tried drivers "nv" and "nouveau" in Xorg.conf, no change.

I can't find any relevant log information, so I can't figure out where to start.

---

### Post by quequotion on 2011-05-31
Tried creating a new user and got the same failure with slightly different behavior.

A new user with an empty home directory can login and load the desktop in all modes, but once the graphics are on the screen everything freezes as usual. 

I can hear the sound of pulseaudio crashing and reloading over and over as well, until everything freezes.

---

### Post by quequotion on 2011-06-05
So I installed Gnome3 from the PPA, hoping to give up on this Unity nonsense....

To my surprise, it made Unity work! Well, somewhat work at least.

Jockey still says my proprietary nvidia drivers are "activated but not in use" which is a lie. The driver most definitely is in use and functioning.

Compiz is in disarray. Cube is working, but cube deformation is not. Settings revert randomly at login... Doesn't make sense.

I can't get applications to use the appmenu-indicator, *except for firefox*. The ONLY application properly using the global menu is firefox. WHY?

Unity doesn't respect the notification area or it's icons, only "indicators" will be shown on any panels.

I deleted a lot of settings and other things because gnome-settings-daemon was segfaulting, giving me an ugly and not-so-functional desktop.

For now I enjoy logging in to "GNOME Classic" (Metacity, Gnome/Compiz) much more than "Ubuntu" (Unity/Compiz) although both are minefields.

Can anybody help here? This is becoming the Fukushima of upgrades.

---

### Post by quequotion on 2011-06-06
Things are making a little more sense today.

My original problem, freezing after login, is gone. I can't mark this thread solved however because I don't know quite how or why this was fixed.

Upgrade recap:

I upgraded rather smoothly using a custom script (the Ubuntu method is not a possiblity for me). Much more so than any previous upgrade.

After solving a few dpendency chains, I rebooted.

Logging into Ubuntu, Ubuntu Classic, or Ubuntu Classic (No effects) never made it to the desktop and froze. Ubuntu (Safe Mode) worked, but used a slow 2d-only generic driver.

Nouveau did no better than nvidia, even after removing nvidia and is blacklist of modules. Nv did no better than Nouveau, which is a complete mystery.

I tried three versions of the nvidia driver from PPAs. No difference.

Added the GNOME3 PPA and upgraded, without explicitly installing gnome-shell.

With the Gnome3 libraries and desktop installed, I found I could log into Gnome Classic and Gnome Classic (No effects) without freeze, but several other outstanding issues.

After fixing a few problems with Gnome by gconf-editor, dconf-editor, and deletion of lots of my personal config files, Gnome began to run somewhat smoothly.

Compiz at 0.9.4 does not run smoothly in any environment, but I was able to test Unity with Compiz/Gnome. On a hunch, I tried logging in to Ubuntu.

Miraculously, it works. It has a lot of problems, but it works. Jockey still doesn't recognize that the proprietary nvidia driver is "in use".

libappmenu.so doesn't exist for Gnome3 yet, so none of my Gnome3 applications will use the global menu while Firefox, Transmission, and a few other non-gtk or gtk2 apps can.

No windows have close, minimise, maximise/restore buttons except when maximised. 

Compiz 0.9.4 has a ton of bugs. Sometimes it won't start at login, leaving me with a window-manager-less and therefore completely useless desktop. Sometimes It misrenders both 2d and 3d objects; like not filling in behind the unity panels or putting the skydome on at the wrong angle and leaving a hole in the cube.

Gnome3 has some issues to. Particularly, I've lost Ubuntu One functionality due to a change in the encryption ABI. I don't think there are any plans to revert this change.

---

### Post by quequotion on 2011-06-12
Update....

Got things running (finally). Took less time than my last Ubuntu upgrade fiasco.

Jockey still doesn't know I'm using nvidia. Whatever.

Found a ppa for libappmenu-gtk3, but this package is misconfigured. Editing the files in /etc/X11/Xsession.d/ got this working for all apps.
 
A little more dconf editing restored window decoration with all three close, minimise and restore buttons.

Compiz is behaving better. Still misrendering from time to time and occasionally taking a long time to load.

Still no Ubuntu One.

Note: GTK3 apps and GTK2 apps will use different themes, so they must be set to the same theme in gconf and dconf. Adwaita has both gtk2 and gtk3 themes that match well.

So, presently I am running Ubuntu Natty with a GTK3 desktop in the Compiz/Unity Shell using proprietary nvidia drivers.

It's been a fun week, but I think I'll get some sleep now.

---

