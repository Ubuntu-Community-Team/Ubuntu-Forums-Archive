---
title: "How to re-install"
date: 2008-11-14
forum: Installation &amp; Upgrades
---

### Post by ticknubbs on 2008-11-14
I had upgraded my dual boot machine from 7.10 to 8.04. so that I could upgrade to 8.10. When I went to 8.04 I could not display to my extra monitor anymore(since my laptop screen is faulty and out of warranty). I had to use the horrible method of squeezing the pin connection to display what was on my laptop screen. Doing so I eventually upgraded to 8.10. Now there are no drivers for anything, wireless, graphics, etc. I have tried to find a solution to this but nothing was found. How could I re-install 8.10 to see if maybe that will help? Any suggestions will be greatly appreciated.

---

### Post by DieB on 2008-11-14
start a terminal ( in Gnome: "Applications-Accessoires-Terminal") and type: > sudo aptitude update && sudo aptitude upgrade
this will update your repositories and then update your installed programs.
(This only works if you got connection to internet).

Otherwise you can download the cd and install - but watch out if you have no seperate /home-partition. for howto see:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

hope it helps

---

### Post by ticknubbs on 2008-11-15
HEY THANKS! Everything Works now!

---

