---
title: "widescreen problem"
date: 2007-07-29
forum: Installation &amp; Upgrades
---

### Post by dnt on 2007-07-29
First please forgive as I am a total Linux noob:)
  I have been trying to install 7.04 and I am not having very much luck. The install all goes well but when I remove the Cd and reboot there is a problem. I get the splash screen but it is offset to the left and I am only able to see the right half of my desktop. I am not able to get to the control panel so I am stumped at this point.
  Like many noobs I have been trying many different distros and it seems like any distro that is based on Ubuntu has this problem. Some other distros do not have this problem. When I use an older computer and a 4/3 monitor I have no problems.
  My system with the widesreen monitor has a AMD4000, 2 gig ram, sata hard drive in removable HD racks and a Nivida 7600GT. I am using a Dell 20 inch widescreen monitor.
  The old system has and AMD 2500, 2 gig ram, IDE harddrive, Nivida 6600 and a Dell 19 inch monitor.
If anyone has an idea I surely need the help.
Thanks, David

---

### Post by Circuit99 on 2007-07-29
Have look here explains how to change resolution:

[http://ubuntuforums.org/showthread.php?p=454217](http://ubuntuforums.org/showthread.php?p=454217)

and here about basics

[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

What you can do is open a terminal and edit your xorg.conf file

easy way

ALT+F2

Then enter in top box

gksudo gedit /etc/X11/xorg.conf

then press run

make backup copy before you chage it.


The alternative is on booting before you log in

Ctrl+ALT+F1

then edit xorg.conf using nano (which I don't like)

Read the first link before decide.

You need to know you moniter frequency range it helps.

Post here you get a solution

Good Luck :popcorn:

---

