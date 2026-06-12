---
title: "Ati fglrx X11 conf problems..."
date: 2007-07-20
forum: Installation &amp; Upgrades
---

### Post by NachoMas on 2007-07-20
Hi all,
I have a weird problem with my X11 configuration that is driving me crazy. I have a radeon mobility 9660 integrated card in my laptop, which I use both at work and at home. At work I have a wide flat panel which I use at 1920x1200, while I home I have a smaller LCD that I can use at 1280x1024.

- First problem: at work, when I shutdown the system and I am at 1920x1200, the X server stops and then the screen goes blank and the computer freezes. I can imagine that it has to do with the console driver not being able to recover itself or change resolution? I really have no idea how to fix it. The only think I can do is change the X resolution to 1280x1024 before clicking on shutdown, and then it works without problem...

- Second problem: I have tried configuring my X11 so that I can use both resolutions depending on which screen I am using, but if I leave the higher res scren entry, my screen at home is unable to display anything and the resolution does not automatically adjust. The only option I have is having two screen entries in X11 and commenting in and out the relevant one whether I am at home or not. I am sure there has to be a better way of doing this!

I am including my xorg.conf file so that you get pinpoint my mistakes and help me out with it!
Thanks in advance!
/Nacho

---

### Post by Circuit99 on 2007-07-23
I hope this helps what I think is happening you have set up for three monitors


Section "Monitor"
	Identifier   "LCD"
	HorizSync    30 - 80
	VertRefresh  60 - 75
    Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "HP LP2465"
	HorizSync    30 - 90
	VertRefresh  48 - 80
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "TV"
	HorizSync    30 - 50
	VertRefresh  60
EndSection


Try disabling one (try TV) of them and see what happens (just put in # before it).


Also in Section 'Screen'


Modes    "1920x1200" "1280x1024" "1024x768" "800x600" "640x480"

This way both have same resolution range

These are only ideas but you can get more info from here


[http://ubuntuforums.org/showthread.php?p=454217](http://ubuntuforums.org/showthread.php?p=454217)


Good Luck !!!

---

### Post by Circuit99 on 2007-07-23
This  is  how to enable CRT output (external monitor/projector) for notebooks (Intel)

[http://ubuntuforums.org/showthread.php?p=454217](http://ubuntuforums.org/showthread.php?p=454217)

I don't know if there is similar way for ATI :???:

---

### Post by Wim Sturkenboom on 2007-07-24
No (simple) solution for the first problem. As a (simpler) workaround you can switch to a console and shutdown from there; if necessary modify the <ctrl><alt><del> combination to do a shutdown instead of a reboot (I have configured my Slackware box like that, but not sure how to do it in the latest Ubuntu releases).

You can try to add *Option "UseEdid" "True"* to the device section. It's my understanding that that should force X to use the monitor capabilities; your monitors probably support it and your TV does not Not sure however.
Further you can consider to place the 1280x1024 before the 1920x1200 as that would be the default resolution for X. When using the big screen, you can simply switch to the higher res using <ctrl><alt><+>

---

