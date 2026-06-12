---
title: "Problem with desktop windows"
date: 2010-04-06
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Thystra on 2010-04-06
OK, so the other day i decided I would try to turn on the fancy desktop effects under appearance.  This was after enabling the NVIDIA hardware driver (HDX 16 laptop, GT 130M).  It didn't work, it tried to search for some drivers and then what happens is that the dialog freezes.  I click OK and it sits there until it has to be force quit to close, effect never enabled.  

Then I started getting a weird window error.  Upon boot up and log in, all windows (firefox, empathy, etc) are missing their top bars, the one with title, minimize, max and close buttons.  the windows are pinned to the top left corner (can't move them) but I can resize them.  I moved the bars to the bottom of the screen so I could see them, and the bar that usually holds all your open applications has nothing in it with several windows open (firefox, empathy, update manager).  Alt Tab between apps doesn't work.  

When I open my home folder, it shows briefly "Opening...." and when the window comes up, it goes out of the task bar.  

I did some searching the other day and found this command:

rm -rf .gnome .gnome2 .gconf .gconfd .metacity

which I have used and then rebooted and it restores to normal settings, but after a boot or two I come back to this problem.  I've tried looking through gconf but I can't seem to find the setting that makes the bars re-appear.  any help would be appreciated.

---

### Post by Thystra on 2010-04-06
it appears to have something to do with compiz, I installed emerald and set up a emerald theme and everything is back to normal following a reboot.

---

