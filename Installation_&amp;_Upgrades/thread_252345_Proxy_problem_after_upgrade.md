---
title: "Proxy problem after upgrade ?"
date: 2006-09-06
forum: Installation &amp; Upgrades
---

### Post by hairygerman on 2006-09-06
Hi all,

I upgraded yesterday from 5.10 to 6.06 using Synaptic. What a mission!!!!!
During the upgrade there were constant messages about icons not being found (for evolution and help in the main toolbar), I was told that the upgrade had failed for postfix, mailx and mantis (and I was asked to report bugs on this). And in the end I am greeted with a simple message telling me that the upgrade was being aborted and my system could be unstable.
Well, all of this aside, I am now unable to start firefox or use any other app from a terminal window because some setting insists on telling these apps to use a (non-existent) proxy.
However, I have figure out that this does not apply when logged through a remote shell or one of the alternative consoles. 
Have tried removing and re-installing firefox, removing squid, looked through pretty much all of the config files for gnome and bash, but I cannot find where this false proxy comes from.

Has anybody out there witnessed anything similar? I am quite happy to provide whatever information is required, although I am currently seriously hampered by the fact that my gnome desktop simply will not allow me to connect to anything outside my own little network.

Help, please !!!!

P.S.: My Ubuntu box runs DHCP and DNS, my internal network uses subnet 192.168.0.x, and every request to load someting from a website or similar is greeted with an attempt to talk to a proxy at 192.168.100.2 (which doesn't exist).

Any help will be much appreciated.
regards

The Hairy German

---

### Post by hairygerman on 2006-09-07
OK, I found where to change the proxy settings. Nevertheless, it is strange that the upgrade modified them to a computer that doesn't even exist on my network.

---

