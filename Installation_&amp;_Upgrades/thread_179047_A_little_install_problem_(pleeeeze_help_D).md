---
title: "A little install problem (pleeeeze help :D)"
date: 2006-05-18
forum: Installation &amp; Upgrades
---

### Post by RobArson on 2006-05-18
ok, so my laptop was dual booting xp and ubuntu hedgehog. So i wanted to upgrade. I got the wiki instructions at [https://wiki.ubuntu.com/BreezyUpgradeNotes](https://wiki.ubuntu.com/BreezyUpgradeNotes).

Basically, i ended up at with tty. I got there after Synaptic finished the upgrades. There was a mention of an upgrade error with Firefox so I rebooted, perhaps foolishly. I didn't get up to changing my repositories or anything passed that.

In tty, I basically can't do anything (i tried emacs, gedit, mozilla) There's some mention of locks i think in the error message.

Can anyone offer advice on how to finish my install (or at least how to get back to my oh so precious gui!? Thanks :D

---

### Post by Sef on 2006-05-19
Can you do Alt F2 (Run Application)?  If you can type gnome-terminal and in the terminal type this in or copy and paste it in:

sudo gedit /etc/apt/sources.list

Copy and paste the list in here.

Likely you will have to reinstall Ubuntu as probably a number of things are broken.

---

### Post by RobArson on 2006-05-19
thanks sef. i did alt f2 and it just gave me another terminal (i have no idea if thats what it was supposed to do :D)

anyways, i tried gnome-terminal and the sudo...

each time i just go this (not exactly copy pasted):

Gtk-warning Locale not supported by C Library
Using the fallback 'C' Locale
Gtk-warning: cannot open display



so unless someone can save me from doing it, i guess i'll just reinstall tomorrow morning. BTW anyone know of anything i should be aware of when i'm reinstalling since I got XP on another partition already and i'm using GRUB?

thanks again :D

---

### Post by PhilOSparta on 2006-05-20
Check this:  [https://wiki.ubuntu.com/GrubHowto](https://wiki.ubuntu.com/GrubHowto)

and  [https://wiki.ubuntu.com/GrubHowto/ChangeDefaultOS](https://wiki.ubuntu.com/GrubHowto/ChangeDefaultOS)

---

