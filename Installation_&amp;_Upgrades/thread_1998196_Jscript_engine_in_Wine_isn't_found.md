---
title: "Jscript engine in Wine isn't found"
date: 2012-06-06
forum: Installation &amp; Upgrades
---

### Post by djahma on 2012-06-06
Hi,
I'm trying to install a windows software called AmiBroker in Wine which requires IE to run the jscript engine used to access is OLE/COM interface. It used to work fine using wine 1.2.2. But since ubuntu 12.04 and wine 1.4, that jscript engine wouldn't work.
From a fresh prefix, I installed everything like I did 18months ago but from within AmiBroker, the scripting part doesn't work; and when I do ```
$wine wscript somefile.js
``` I get an error saying jscript engine not found.

When I delete the .wine folder and paste the old one I've been using for 18months instead, oddly enough, the scripting part works within AmiBroker, but not when I do "$wine wscript somefile.js": same "jscript engine not found" error

I added wine ppa, removed wine 1.4 to install 1.5 and repeated to steps above. In the end the results were the very same.

I removed everything wine related from my computer and tried to install wine 1.2 but it was wine1.4 which got installed. Anyone knows why "$sudo apt-get install wine1.2" installs wine1.4 instead?

Eventually, I installed my stuff in a VirtualBox but on my dual core laptop with only 2G of ram and my multi tasking habits, the computer gets really slow:frown:

It used to be such a cool work environment I had there, with everything windows related working in wine, the computer was "fast", and all my scripts and software were smoothly integrated.
I'd need to get a wine1.2 package to make it work again, or a solution to get the jscript engine to work again in wine. Has anyone succeeded at running a .js file under wine1.4 or above?? if yes, I'd love to know how you do that(I've already tried winehq forums but no one there had any solution for me)

thanks in advance
G.

---

### Post by ankara on 2012-06-22
I'm currently looking for the solution to this also, after an upgrade, my reaper DAW stopped working with wineASIO, and i want to downgrade back to wine1.2 and a previous version of reaper where everything worked fine. installing wine1.2 resulted in wine1.4 being installed.

---

