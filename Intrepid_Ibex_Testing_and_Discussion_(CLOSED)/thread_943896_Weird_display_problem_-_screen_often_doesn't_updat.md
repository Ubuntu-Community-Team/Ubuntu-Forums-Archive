---
title: "Weird display problem - screen often doesn't update"
date: 2008-10-10
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by tim1 on 2008-10-10
I am experiencing a weird bug on my laptop where the screen, or usually party of the screen don't update.

It's hard to explain but basically when I do something that changes part of the screen (or rather should change) the area in question keeps displaying the old content. When I move with the mouse over the area in question some small parts get updated, like a link or a button that I hover. When I click inside the window or move it the display updates and everything is fine.

This happens with all programs I am using which are mostly GTK but also with VLC.

I am using the closed Nvidia driver, but i also use that one and the same software on my desktop PC, which works fine.

I have a Dell XPS M1330, nvidia 8400gs, core 2 duo

The issue is incredibly annoying and using my laptop and especially surfing the web isn't fun anymore, I hope someone can help me getting this fixed.

I attached a screenshot to show how my System Monitor looks like when I switch from the 'Resources' to the 'Processes' tab.

---

### Post by jamlam on 2008-10-10
I can confirm I'm also getting this on a Lenovo T61p with Nvidia graphics. It looks like some kind of video memory corruption or something along those lines, and seems to happen in mainly in Firefox, but it does affect other apps as well. The symptoms of this are the screen not updating when it should do, e.g. if I switch tabs in Firefox the screen doesn't change until I mouse over certain objects, then that section will update to display correctly. I've tried taking a screenshot, but that seems to cause the screen to update so the screenshot looks fine. Anyone got any ideas?

---

### Post by plun on 2008-10-10
Check and test this from nVidias forum

[http://www.nvnews.net/vbulletin/showthread.php?t=118088](http://www.nvnews.net/vbulletin/showthread.php?t=118088)

Just the Quickstart in the beginning.  8400 GPUs seems to be troublemakers.

---

### Post by tim1 on 2008-10-10
I tried the workaround but it doesn't work

---

### Post by FuturePilot on 2008-10-10
[https://bugs.launchpad.net/bugs/269904]("https://bugs.launchpad.net/bugs/269904")

Very annoying bug...
:(

---

### Post by kulebreeze on 2008-10-11
Hi Tim1,
Am having the exact same problem and its driving me craazy. i looked at any files i think might be messed up and nothing seems to help. every window on my laptop i have to move the mouse over the parts thats not updated. I sure wish they can fix soon, but i will keep looking an if anything appear i will post it....

---

### Post by psyphen on 2008-10-11
I'm having the exact same problem.

I posted here before realizing another thread existed.
[http://ubuntuforums.org/showthread.php?p=5943979#post5943979](http://ubuntuforums.org/showthread.php?p=5943979#post5943979)

I run Intrepid on an ASUS M51S that has a GeForce 9500M GS in it. I'm running version 177 of the Nvidia drivers. None of the fixes are working yet.

---

