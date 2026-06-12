---
title: "Jaunty upgrade experience (very good!) and Bluetooth DUN"
date: 2009-03-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by dro0g on 2009-03-27
I upgraded my Dell Latitude D630 to Jaunty a few days ago. The upgrade process was flawless, the only thing that was borked was flash (had to remove/reinstall in Synaptic.) I've upgraded at Alpha 5 or 6 for the past few releases and I have a lot more confidence these days than even just a few years ago where I knew an upgrade would mean X weirdness and much time sorting out errors and dependencies. Great job to the Jaunty team!

I'm using an Intel GM965 graphics card so I of course wanted to try UXA and ran up against the alpha blending bug. I'm now running packages from the xorg-edgers ppa and patched mesa libs from someone else's ppa that fixed the alpha blending bug. 

X is running much more smoothly with compiz. It's also working a lot better with Wine/Crossover. I had to enable direct rendering (when it was turned on the bug was still happening) I also screwed things up a bit by enabling vsync in compiz settings.

At some point in Intrepid I had installed a patched mesa that included the fix for the 2048x2048 virtual resolution limit on the 965. That seems to be back in mesa master so while I can use apps across both monitors, Compiz corrupts part of the desktop background.

**Things that I'm still working on**

_Docking_ 
I switch between using the laptop screen, using a docking station with one monitor and using a docking station with two monitors at different resolutions. xrandr rocks and I'm glad I don't need to maintain separate xorg.conf's like I used to to do dual monitors, but I've yet to find a good way to dynamically switch resolutions coming out of suspend or when docking. 

Previously I was just using CTRL-ALT-BACKSPACE to restart X. I've tried the whole ALT-SysRq-k thing but that doesn't seem to work. If I remember to logout before undocking/suspending, GDM seems to do OK detecting something's changed, but I can't figure out what it (or gnome-settings-daemon) is actually doing so I can do the same thing when coming out of suspend. A keyboard shortcut doesn't seem to do anything, I'm assuming because the screen is locked. I can run
```
sleep 20;xrandr --output VGA --auto
``` 
then quickly shut the lid (to suspend) and dock and it will switch OK.

_Bluetooth 3G DUN with Blueman and NetworkManager_
In Intrepid I had mobile broadband working with NetworkManager using a Bluetooth connection to my Verizon Blackberry Curve. It totally rocked (I'm using it from the train right now to write this post from a netbook) I spent a good 4 hours playing around with Blueman, NetworkManager, HAL and udev. I'm running Blueman and NetworkManager from their respective PPAs.

It looks like the issue is that NetworkManager switched from using HAL to detect 3g modems to using udev. Blueman both has a bug in the HalManager.py (fixed by grabbing the file from svn) and it doesn't seem to put into udev whatever NetworkManager is looking for. I tried manually putting in settings via /etc/udev/rules.d (creating a rule file) per one of the posts in the bug report, but while I could get it to detect I couldn't get it to work. I don't really have a clear understanding how udev/hal and rules files work and interact, but nm-probe-modem seems to detect the modem OK. I saw a post on the NetworkManager list that seems to indicate it's having some problems with detecting USB modems as well right now, so hopefully this will all be sorted out soon.

Here is the bug report: 
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/345060](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/345060)

---

