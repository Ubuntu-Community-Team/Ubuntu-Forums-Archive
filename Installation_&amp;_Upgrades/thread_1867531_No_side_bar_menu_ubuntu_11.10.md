---
title: "No side bar menu ubuntu 11.10"
date: 2011-10-23
forum: Installation &amp; Upgrades
---

### Post by nkbatsi on 2011-10-23
Hello, I 've just upgraded to 11.10, everything went fine , but a couple of days later I pushed my machine a little too much   and I lost the side bar menu on the left and the top bar (time, date, user, internet connection icon, bluetooth icon etc.)

How can I bring back these items? Thank you for reading

---

### Post by dino99 on 2011-10-23
to get the bar back, from a terminal:

gnome-panel --replace (if you are logged as gnome-classic)
unity --reset (if you are logged as ubuntu)

if the side bar is not back, then you need alacarte be installed, then right click on "Applications" on top left corner and set the menu preferences (to move the bar to either top, bottom, left, right)

---

### Post by nkbatsi on 2011-10-23
I did :
**unity --reset**
 
logged in as ubuntu and nothing happened, the same almost empty screen, uninstalled alacarte (which was already installed) and re-installed it and did
[B]
unity --reset [/B]once again  nothing happened, still getting the same empty screen

Forgot to say that this happens only for the root not for other users whose terminals shoe up fine

---

### Post by nkbatsi on 2011-10-23
Ok just found out what it was, Unity plugin was unticked in CompizConfig, 
returning to Gnome now, Thank you very much!

---

### Post by coryr545 on 2011-10-25
how did you do that because i accidentally did the same :/

---

### Post by bayerman11 on 2011-10-25
@[coryr545]("http://ubuntuforums.org/member.php?u=1328055")
i had the same problem.
I was able to open a terminal window with alt+ctl+t
and in terminal I ran:
 **ccsm**  
 (user@computer:~$ ccsm)
from there you can enable the Unity plugin

---

### Post by nkbatsi on 2011-10-27
> **coryr545 said:**
> how did you do that because i accidentally did the same :/

Log in as GNOME classic open a window, select filesystem and search for compizconfig.
You 'll find  a file named **CompizConfig Settings Manager**, open it, scroll down to **Desktop** and tick **Ubuntu Unity Plugin**, come back if you can't make it, good luck!

---

### Post by pierreu1 on 2011-12-16
I had the same --or a similar-- issue and I solved it by left clicking on the little wheel located right of the username/password box, when one logs in Ubuntu (with username and password).

Just to be clear, I think that I had a menu, but no access to any app., including the terminal.

I recently upgraded from Natty and I had installed, both gnome menu and Cairo-dock menu. 

There are several options given:

Ubuntu 2D returned the unity look and it loaded faster.

Cairo-dock with special effect opened, but I had first to agree to try using open GL (there is a little box that you can tick to make that a permanent, default choice). I was surprised it worked actually, because I thought my computer didn't have much of a graphic card (actually the graphic card at the moment is rated as "unknown"! :) . It was slow loading at first. And, it is actually slow loading, even after I cleaned my desktop. I have 1 GB ram and a 1.86 single core Intel. 

I suspect the no-effect Cairo dock would work as well. I have not tried yet.

BTW, there is a recovery option, which I suppose could let deal with the issue in a recovery mode, I think.

I hope this was the right place to post this. If not, let me know and I will post if somewhere else, because --at first-- I was a bit panicking.

---

