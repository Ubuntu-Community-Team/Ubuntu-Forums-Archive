---
title: "Completely baffled"
date: 2005-09-11
forum: Installation &amp; Upgrades
---

### Post by elky10 on 2005-09-11
Hi, I'm totally new to Linux, but I really want to try Ubuntu out.  I decided to use the live cd to check if my comp can handle it, but something's wrong.  I get all the way past the configuration part, to the part where the list of checks comes down, and [ok] or [fail] is printed beside each one.  All of them say okay, and when that finishes, my comp crashes.  The screen goes black with a small blue square on the left side.  When I press a key, the black goes away, and a window is printed on the screen saying that there was a problem starting my x-session, and would I like to see a log.  The only problem is, I can't select yes or no, because although the window is on the screen, a welcome message and console has been printed on top, and any input is given to the console.  Also, the console doesn't seem to stop correctly at the edge of the screen.  It's hard to explain, but each new line seems to begin at a farther place on the screen, wrapping itself around, until it gets to the end and restarts at the left edge.  I can use the console just fine, but it's hard to read.  Finally, when I type x-session-manager, which is the only thing I could think to type, it says:

{x-session-manager:#####:} Gtk-WARNING **: cannot open display

Those numbers increase by one every time I try this command.  I'm totally confused, and would really like to use Ubuntu.  If it helps, I'm using a Pentium III, with an Nvidia Riva TNT graphics card.  Thanks!

---

### Post by mlomker on 2005-09-11
I'd speculate that it isn't detecting your video card properly for some reason.  I'd recommend trying another brand of liveCD.  Knoppix is a good one to use as a test.  My recommendation is to pick a distribution that works on your machine out of the box until you know enough linux to make anything that you want work on you machine.  MEPIS is also worth looking at.

---

