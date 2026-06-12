---
title: "Upgrade fail: Unity must be configured to run manually"
date: 2011-10-16
forum: Installation &amp; Upgrades
---

### Post by cro on 2011-10-16
I followed the upgrade path a couple of days ago to upgrade from 11.04 with Gnome 2.32 to 11.10 with Unity (only because I've not yet managed to figure out how to build Gnome 2.32 on Oneiric)

Once the upgrade completed, I ran into the following issues:

* Unity did not run. I could log in, but no panels at all. It was fortunate I has cairo-dock running so I could actually open a shell and run CCSM. Of course, no window borders so no way to switch between apps.
* I could not enable the Unity plugin in ccsm (all options disabled) unless I ran ccsm as root, at which point any changes were applied for the root user, not my user account.
* Manually enabling the Unity plugin makes the Unity plugin run in every single desktop manager I log in to that also uses Compiz.
* To make Unity run in Unity mode, I had to add both Unity and Compiz to the list of startup applications, otherwise they just wouldn't sart
* Doing this means Unity also runs when I run gnome-fallback
* For some reason, the default colourset and window control icons set by Unity are the only ones that appear in any other desktop environment, but with a strange mix - application controls (title bar, control icons etc) have the Unity "light" theme colouring, but application window chrome (menu bars, inner title bars, status barss etc) have the Unity "dark" coluring. This is persistent in Xcfe when running Gnome applications.
* Running Unity and Unity 2D have the same result, and after about 5 minutes the entire OS freezes requiring a hard poweroff.
* resuming from Suspend dims the display to 20% then immediately goes into hibernate mode. I then have to resume from hibernate to get the computer working again.
* The mute and wifi softkeys on my laptop no longer work. Mute works, but mutes 3 of the audio channels (master, front, speaker). Unmute only unmutes one of the 3 (master), leaving me to manually unute the other 2 (front, speaker) before I get sound back. The Wifi button works to turn wifi on and off, but unlike in 11.04 it doesn't toggle it's lit state anymore.
* For some reason upgrading to 11.10 installed grub1.9 with a debian background image?
* Bootup takes 4 times longer than it used to, and I get a black screen between the grub menu and lightdm starting

Effectively I've gone from a computer with good working environment that I could use effectively for work on a day to day basis (Ubuntu 11.04+gnome2.32) to a non-working environment (11.10+unity) where I have now spent the better part of two days reconfiguring and trying to sort out various issues manually, simply by selecting dist-upgrade.

I would welcome suggestions as to how I can solve the above problems (apart from a complete reinstall - if I need to do this I'm going back to 11.04 permanently.)

And I would especially welcome any help in compiling Gnome 2.32 to work with Ubuntu 11.10 or the 3.x kernel. I tried using jhbuild but most of the required packages have been removed from the Ubuntu repositories.

---

### Post by dino99 on 2011-10-16
gnome3 have no relationship with gnome2, its built from scratch, so the look & feel is very new, and lack a bunch of features right now. Unity is a 3D shell, is your hardware able to run it ? Gnome-shell & gnome-session-fallback are an alternative and look closer to gnome2. But you might deeply clean your system (deborphan/bleachbit) to purge old config/settings, or better do a clean fresh install via unetbootin + mini-iso

By the way everything is already ready into the archives, so why do you want to compile from sources ?

---

### Post by cro on 2011-10-16
> **dino99 said:**
> gnome3 have no relationship with gnome2, its built from scratch, so the look & feel is very new, and lack a bunch of features right now.

At which point it is unuseable in a professional or commercial environment.

> **dino99 said:**
> Unity is a 3D shell, is your hardware able to run it ?

8-core Intel i7, 4Gb RAM, NVidia GT-230M with 1Gb of dedicated graphics RAM. Yes, perfectly capable of running Unity 3D.

> **dino99 said:**
> Gnome-shell & gnome-session-fallback are an alternative and look closer to gnome2. But you might deeply clean your system (deborphan/bleachbit) to purge old config/settings, or better do a clean fresh install via unetbootin + mini-iso

Whilst reinstallation is a solution to the above problems, it's not a solution that allows me to retain the 3.x kernel.

> **dino99 said:**
> By the way everything is already ready into the archives, so why do you want to compile from sources ?

I want to compile Gnome 2.32 from source. The Gnome2 desktop environment is one that I am failiar with, and is also the environment that performs the best and has the greatest measurable impact on my professional productivity. My normal work environment is 5 workspaces, dual high-resolution monitors, and typically more than 50 open windows (not including tabs) spread across these workspaces.

Unity2d/Unity3D and Gnome3 all actively work to hinder my effectiveness by forcing me into a particular way of working, and by making it difficult for me to manage windows, applications, organisation of logical program, and perhaps most heinously, all three of these environments actively hide information about running programs from me.

---

### Post by cro on 2011-10-16
> **cro said:**
> * For some reason, the default colourset and window control icons set by Unity are the only ones that appear in any other desktop environment, but with a strange mix - application controls (title bar, control icons etc) have the Unity "light" theme colouring, but application window chrome (menu bars, inner title bars, status barss etc) have the Unity "dark" coluring. This is persistent in Xcfe when running Gnome applications.

This seems directly related to running `compiz --replace ccp` at startup. If I kill compiz, the window manager theme is used. If I run Compiz, it uses whatever Unity's theme is, and doesn't let me change it.

---

### Post by cro on 2011-10-16
> **cro said:**
> This seems directly related to running `compiz --replace ccp` at startup. If I kill compiz, the window manager theme is used. If I run Compiz, it uses whatever Unity's theme is, and doesn't let me change it.

OK, fixed this one. Installed `gnome-tweak-tool` and this now lets me change the window chrome.

---

