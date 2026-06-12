---
title: "Lucid : Panel issues"
date: 2010-03-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Gonchos on 2010-03-14
I've just updated to Lucid and the only thing bugging me are  panels. 

     "Indicator panel session" applet  (log in, shut down ...) appears as "No indicators", and trying to delete/configure it completely freezes my computer.

     "Notification area" only shows wireless signal and, sometimes, battery info. Volume control is completely gone.

     Is this a known bug or something I've screwed?

     Thanks!

---

### Post by 23meg on 2010-03-14
The "no indicators" problem had also occurred earlier this cycle; make sure you have all related packages up to date, and wait a short while for new updates. If it persists, file a bug report.

The other problem seems to be that you don't have the indicator applet in your panel. Try adding it.

---

### Post by Gonchos on 2010-03-14
Problem 1: updated everything, and the applet still show "No indicators" I've created a new applet in a new panel and it still crashes the computer.

Problem 2: In karmic, a single applet (notification area) showed internet connection, battery status and volume. Now it only shows internet and, sometimes, battery. I can toggle volume from system > preferences > sound.

is there a way of removing applets from panel other than right click > remove?

thanks!

---

### Post by Madspyman on 2010-03-14
If you've deleted the indicator applet add the command gnome-volume-control-applet to your startup applications. Restart and your volume icon should be back in the panel.

---

### Post by 23meg on 2010-03-14
[QUOTE=Gonchos]Problem 1: updated everything, and the applet still show "No indicators" I've created a new applet in a new panel and it still crashes the computer.[/QUOTE]

That sounds like it may be a bug.

[QUOTE=Gonchos]Problem 2: In karmic, a single applet (notification area) showed internet connection, battery status and volume. Now it only shows internet and, sometimes, battery. I can toggle volume from system > preferences > sound.[/QUOTE]

As I said, that's probably because you're missing the indicator applet and/or some related packages. Try adding it to your panel and installing indicator-sound.

[QUOTE=Gonchos]is there a way of removing applets from panel other than right click > remove?[/QUOTE]

Which specific ones are you trying to remove? If you want to disable certain components of the indicator applet, those are not applets by themselves. You can remove them by removing the corresponding package (indicator-sound, indicator-messages, etc.)

---

### Post by Gonchos on 2010-03-14
Sorry, I meant "Indicator panel session", I've three of them in my top panel now, and any miss click locks the whole system

---

### Post by Gonchos on 2010-03-14
Solved!

Thanks for the info on the volume applet, it worked great!

And on the session applet, I completely deleted all packages, reinstalled them, reloaded the whole gnome-panel, and now it's working fine.

Thanks!

---

