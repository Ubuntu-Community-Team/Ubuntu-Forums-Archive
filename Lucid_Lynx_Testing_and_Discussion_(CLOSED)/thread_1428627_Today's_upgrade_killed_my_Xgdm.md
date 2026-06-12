---
title: "Today's upgrade killed my X/gdm?"
date: 2010-03-13
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by FrancoNero on 2010-03-13
Okay so I ran updates this afternoon, and it was all fine, but then there were some updates later in the evening, and upon restart (must have something to do with Plymouth as I now FINALLY see something that resembles a splash screen) I end up with a terminal screen for login, but not much else.... how do I get out of this? Do I have to manually start X or something? Please help, don't wanna kill off my Lucid partition, I wanna follow along with the development

---

### Post by Tompalaz on 2010-03-13
You could type startx or sudo gdm restart after you logged in?

I get to a terminal likeish screen with output errors from plymouth. I have to press enter, it then restarts gdm and it works fine.

---

### Post by kansasnoob on 2010-03-13
I have to login (username then password) and then startx, but I noticed my CPU was running warm (not hot, but too warm) so I checked in System Monitor and X was pulling 70% to 80% of my CPU doing nothing but browsing these forums, so I'm out of there for now.

I multi-boot so I just booted into another OS.

---

### Post by giorsat on 2010-03-13
I have the same problem with nvidia driver installed. The updates breaks my boot. Xorg doesn't start anymore.
I had to reinstall everything and the only chance (after 3 complete reinstallation because I tried the various updates) is to stay away from the updates for the moment

---

### Post by taavikko on 2010-03-13
From plymouth's changelog 0.8.0~13
```
* I'm aware that if you see the TEXT plugin, it's possible for Enter to
    still crash the X server for some people.  I will be opening a new bug
    for this, and would appreciate details from people affected.

  * If you have issues with Enter crashing the X server, and you see a
    GRAPHICAL plugin, check that gdm is up to date - if it is, please
    file new bugs.

  * I'm also aware of an issue where after boot, rather than seeing an X
    server, you see the ordinary "login:" getty screen.  Pressing Alt+F7
    should take you to X.  I will be opening a new bug for this, and would
    appreciate details from people affected.
```

So just sit tight and check the changelogs when your issues has been solved, they're worked upon.

---

### Post by teh603 on 2010-03-13
Given how much they're working on it, they should be able to make the milestone in time for the beta freeze. We've had at least two updates to Plymouth in the last twenty-four hours, which is more than we had in the last month or so.

---

### Post by victor9098 on 2010-03-13
> **taavikko said:**
> From plymouth's changelog 0.8.0~13
```
* I'm aware that if you see the TEXT plugin, it's possible for Enter to
    still crash the X server for some people.  I will be opening a new bug
    for this, and would appreciate details from people affected.

  * If you have issues with Enter crashing the X server, and you see a
    GRAPHICAL plugin, check that gdm is up to date - if it is, please
    file new bugs.

  * I'm also aware of an issue where after boot, rather than seeing an X
    server, you see the ordinary "login:" getty screen.  Pressing Alt+F7
    should take you to X.  I will be opening a new bug for this, and would
    appreciate details from people affected.
```

So just sit tight and check the changelogs when your issues has been solved, they're worked upon.

The 'alt-F7' option above got me working again. I was very worried there for a while.

---

### Post by FrancoNero on 2010-03-13
thanks everyone, will try the above mentioned things and wait for updates. It's coming along nicely now, I think the Beta will look pretty slick. Even though (off topic now) Empathy is the biggest disappointment ever, I mean that app is (aside from the nice integration) rather useless, and not half the messenger Pidgin is

---

### Post by pyedog on 2010-03-23
I had the same problem as this, the problems ended up being something probably not, but possibly, related to your's FrancoNero.

I carried out the updates and restarted, then my X server had disappeared. I later realised it was due to the fact that I had also ran the following command at a terminal to remove empathy and evolution:

> sudo apt-get remove empathy evolution*

For some reason this inadvertantly removed a few other packages such as gnome-sessions and gnome-applets without me realising.

As I said, quite possibly unrelated, if so then I apologise for my noobishness.

---

