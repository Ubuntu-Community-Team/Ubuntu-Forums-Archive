---
title: "Secure"
date: 2005-03-28
forum: Installation &amp; Upgrades
---

### Post by silentstriker on 2005-03-28
Hello,

On my machine, I want to block all incoming traffic, and all outgoing traffic except port 22. 

I use SSH to tunnel and browse the web that way, so only that port needs to be active.

I also have several eth connections (eth0 through eth4), though only one is active at a time (depending on my location...work, home, school, etc).  But this should apply to all eth connections.

I want this to happen everytime I start the computer, but I want a quick way to shutting it off.

Is this possible?

Any help is GREATLY appreciated.  I know I have to modify iptables somehow, but I am a newb and the iptables help file went over my head.


-Thanks!

---

### Post by alastair on 2005-03-28
IPTables (netfilter) is what you want. There are many easier ways to set it up than using the raw command to add/modify rules. One way to do it is a tool like "shorewall". Perhaps worth looking at that :

shorewall (package)
[www.shorewall.net](www.shorewall.net)

---

