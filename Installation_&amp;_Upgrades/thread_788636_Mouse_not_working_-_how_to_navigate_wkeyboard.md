---
title: "Mouse not working - how to navigate w/keyboard"
date: 2008-05-09
forum: Installation &amp; Upgrades
---

### Post by zero_koop on 2008-05-09
I just upgraded to Heron and my mouse no longer works!  I get a cursor but no movement (I automatically log in).  I think I had originally modified my xorg file in order to get my mouse side buttons to work, but right now I can't figure out how to open the file without using my mouse!  How can I either open up a terminal without a mouse and or use the menus up at the top in the taskbar without clicking on it with my mouse.  From there I will see what I can do to fix my mouse, but at least get me started on that if you would.  Thanks.  If you have any suggestions at all for what I could do for my mouse let me know that as well.  Thanks.

---

### Post by snow_56767 on 2008-05-09
Hi,
   To get to the menus with the keyboard is easy. 
You just have to push Alt-F1, then use the arrow keys to navigate.
 To close a window use the Alt-F4 key combo

[ATTACH]69452[/ATTACH].

---

### Post by zero_koop on 2008-05-10
Thanks Snow.  I was able to open up a terminal and get my xorg file edited.  The problem was that I had been using "evdev" as my mouse driver which I did according to these instructions: [http://ubuntuforums.org/showthread.php?t=219894&highlight=run+program+startup]("http://ubuntuforums.org/showthread.php?t=219894&highlight=run+program+startup")
This worked well for the past, but apparently now the default driver of Hardy Heron supports more buttons on the mouse!  Yay!  My guess is that the upgrade process either removed my evdev driver or it is no longer compatible.  Maybe I'll look into it, but for now my mouse is working.  Thanks for you help.  I just never really use keyboard shortcuts that often, but I guess now I have a reason to learn. :)

---

