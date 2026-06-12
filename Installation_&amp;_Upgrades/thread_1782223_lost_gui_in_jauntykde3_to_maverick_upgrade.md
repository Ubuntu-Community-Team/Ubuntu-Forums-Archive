---
title: "lost gui in jaunty/kde3 to maverick upgrade"
date: 2011-06-14
forum: Installation &amp; Upgrades
---

### Post by dochawk on 2011-06-14
I seem to have made a hash of moving a machine from jaunty to maverick.

It used the kde3 remix, and pearson's site seems to be bouncing up and down, mostly down, for that at the moment.

I've ended up with a machine that is console only.

I've tried installing ubuntu-standard, which put a bunch of things on, but still no GUI.

staying with KDE3 would be nice, but I don't have time to mess with it. I find KDE4 painful, and have been put off by the ideological "purity" that caused the gnome split since its inception.

I guess that leaves me with Unity.

But how do I get the bloody thing up.

Heck, xdm & fvwm sounds pretty good right now, too.

:)

Help!

thanks

hawk

---

### Post by dochawk on 2011-06-14
I should mention that I had to use "dpkg-divert --remove" a few times while getting packages to upgrade, as there were nonexistent diversions that it couldn't handle.

---

### Post by ivanovnegro on 2011-06-14
Honestly, the easiest thing would be a fresh install from scratch instead of this painfully upgrade method to all versions between. Also it is faster.

---

### Post by MAFoElffen on 2011-06-15
> **dochawk said:**
> I seem to have made a hash of moving a machine from jaunty to maverick.

It used the kde3 remix, and pearson's site seems to be bouncing up and down, mostly down, for that at the moment.

I've ended up with a machine that is console only.

I've tried installing [COLOR=Teal]ubuntu-standard[/COLOR], which put a bunch of things on, but still no GUI.

staying with KDE3 would be nice, but I don't have time to mess with it. I find KDE4 painful, and have been put off by the ideological "purity" that caused the gnome split since its inception.

I guess that leaves me with Unity.

But how do I get the bloody thing up.

Heck, [COLOR=Green]xdm[/COLOR] & fvwm sounds pretty good right now, too.

:)

Help!

thanks

hawk
I think that you might have some confusion on package names.  

To install the package for the GUI part of Ubuntu is
```

  sudo apt-get install [COLOR=Teal]ubuntu-desktop[/COLOR]

```Which will install everything Ubuntu related on top of the basic system.  

Subsequently, the desktop packages are ubuntu-desktop, kubuntu-desktop, xubuntu-desktop, lubuntu-desktop, etc.   Kubuntu uses KDM.  Ubuntu and Xubuntu uses GDM... Ubuntu 11.10's default DM is planned for LightDM. (we're testing that now.)

I've got all 4 desktos concurrently installed on a test box here.  After it installs, since you are currently installed on Kubuntu now, the first time it boots, it will popup a dialog box and ask you which Window Manager you want to use as a default (because you will have multiple DM's installed), select GDM.  (You can change that default later if you choose.)

When GDM starts, when you select the Username > At the same time the Password dialog box appears > Look at the center of the bottom screen bar... there will be a drop down box that will appear in that bar for you to select which desktop you want to run (Kubuntu, Ubuntu, Ubuntu Classic, etc.).  Select what you want, enter your password and continue.  The default is which you selected last.

Remember to run updates after it installs.
```

sudo apt-get update && sudo apt-get upgrade

```Since Kubutu and Ubuntu have some different default desktop applications, you will notice that the menus will show all of them that are installed. Remember that some KDE app's will not run in Gnome and vica versa.

"[COLOR=Green] xdm[/COLOR] " is a piece of Xorg's (freedesktop) X11 system that is a really basic, no frills X-windows windows manager.  This would be a no-frill basic desktop that you would have to configure pretty much on your own.

---

