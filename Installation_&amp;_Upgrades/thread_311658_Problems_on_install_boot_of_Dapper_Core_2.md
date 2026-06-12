---
title: "Problems on install boot of Dapper Core 2"
date: 2006-12-03
forum: Installation &amp; Upgrades
---

### Post by clownius on 2006-12-03
Ok after much frustration and compiling my own kernel out of desperation on another machine. I can now load 6.06 on my Core 2 sytem.  Unfortunatly i cant get the GUI to work.

Specs are
Core 2 Duo E6400 2.13Ghz
Intel DG965WH motherboard
1Gb (2*512Mb sticks) DDR2 RAM
80Gb SATA HDD
PATA DVD burner that i will soon replace

After it tried to boot GUI i get a flash
tried Xstart and get


```
X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.12 i686
Current Operating System: Linux (computername) 2.6.19-(name of my compile) #1 SMP Sun Dec 3 20:29:44 EST 2006 i686
Build Date: 16 March 2006
     Before reporting problems, check http://wiki.x.org to make shure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting, (++) from command line, (!!) notice, (II) informational, (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Dec 3 22:54:36 2006
(==) Using config file: "/etc/X11?xorg.conf"
(EE) No devices detected.

Fatal server error:
no screens found
XIO: fatal IO error 104 (Connection reset by peer) on X server ":0.0" after 0 requests (0 know processed) with 0 events remaining.
```

Id really love my GUI back so if anyone can point out where ive messed up or a fix id be extrmely happy.  Ive had this computer for almost a week now and really wanna use it lol

---

### Post by TrendyDark on 2006-12-03
I suggest trying to install Edgy. There's really little to no difference (unless you need the ndiswrapper packages to work), and I have successfully installed (and completely messed up) Ubuntu Edgy 3 times now :)

I have a Core 2 Duo E6600, Gigabyte DS3 P965. The only way I can install, though, is by hitting F6 at the first screen and adding the option "all-generic-ide", but you should be good if you don't have a Intel P965 Chipset

---

### Post by clownius on 2006-12-04
Unfortunatly i have the displeasure of owning a G965 series motherboard which is supported even less than than the P965 series board (i know its hard to believe this is possible)
No version of Kubuntu got past booting the kernel until i compiled my own kernel for it.  
Unfortunatly after more struggles and reading it apears my onboard graphics card isnt supported nor is my IDE controller.  I have an adapter comming in for my DVD Burner so i can use that again but i cant really afford a new graphics card until payday so im shelfing by far my fasted computer until i can afford a new video card :(
Note: I have the sinking feeling i may have stuffed up my kernel build as vesa and vga modes are not working so im going to try another compile on that and see if i can get vesa or vga mode going until my graphics card.

Add to the list of unsupported devices my Onboard network card.  I do have a spare of those so easily fixed :)

---

