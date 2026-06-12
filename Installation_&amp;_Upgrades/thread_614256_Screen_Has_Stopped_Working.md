---
title: "Screen Has Stopped Working"
date: 2007-11-15
forum: Installation &amp; Upgrades
---

### Post by EvansLight on 2007-11-15
After i spent all morning trying to get Ubuntu installed (took ages, installer kept freezing, and yes i was even using the alternate cd text installer), i was working on getting it customized to my needs.

I thought that this was it, i was done with everything, now i could just sit back and enjoy my install of linux. Oh now it couldn't be that easy now could it!! I was messing with the appearance, and went to the alst tab of that window and saw the thing i think it was about having some nicer effects for the desktop? 

i cant tell you for sure what it was i was messing with because now my screen has stopped working. When i restarted it after it wanted to download and install a new nvidia dirver, everything was looking fine until it got to the point where it would go to the screen for me to log in. When it hits that screen, after ubuntu loads, the screen just turns off completely. 

I don't even know how to proceed with this. It took all night to get this thing installed, i really don't want to have to do it again, i will if i have to, but i really don't want to.

Any help would be much appreciated.

---

### Post by stevenwscott on 2007-11-16
What version? 7.10 spins cpu around the "configuring apt"section", particularily if you're behind a proxy, and regardless of if you specify a proxy server via network connections, or command line "export http_proxy=http://firewall:80/" - I found a quick way out is to ifdown the ethernet adapters to move it along. 
  The screen deal is probably a goofed Xorg configuration. I have found that ubuntu is not very good at Xorg configurations, and will indeed render you monitor useless until you can fix the X configuration in /etc/X11(much reading required - welcome to Linux!).

  How to bail out is when the screen goes black, hit CTRL-F1 to get to a simple command prompt(know it, love it, it will save your a$$). From there you can check /var/log/ for messages from Xorg to see what the problem is. I would look at the "modes" in the xorg config for the monitor. Good luck!

SWS

---

### Post by EvansLight on 2007-11-16
> **stevenwscott said:**
> What version? 7.10 spins cpu around the "configuring apt"section", particularily if you're behind a proxy, and regardless of if you specify a proxy server via network connections, or command line "export http_proxy=http://firewall:80/" - I found a quick way out is to ifdown the ethernet adapters to move it along. 
  The screen deal is probably a goofed Xorg configuration. I have found that ubuntu is not very good at Xorg configurations, and will indeed render you monitor useless until you can fix the X configuration in /etc/X11(much reading required - welcome to Linux!).

  How to bail out is when the screen goes black, hit CTRL-F1 to get to a simple command prompt(know it, love it, it will save your a$$). From there you can check /var/log/ for messages from Xorg to see what the problem is. I would look at the "modes" in the xorg config for the monitor. Good luck!

SWS

yea i started guessing it was going to be fun. I need to, and want to learn all this eventually, but for now i need to start somewhere a bit easier :P I just went ahead and re-installed. Luckily it went through first try this time.

and it was "configuring apt" section that kept freezing. Now to figure out how to use the printer on my windows based network XD

---

### Post by stevenwscott on 2007-11-16
That works too! :)

   Always remember the non-graphical terminal is available when X is running, though - That's what the CTRL-F1 get's you. Believe me, I recently managed to get dual-head monitors working under Ubuntu, and much time was spent using CTRL-F1 to bail out of incorrect video settings - finally had to manually define stuff in /etc/X11/xorg.conf.

   Have fun!

SWS

---

