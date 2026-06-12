---
title: "Fortune / Fortune-mod on Ubuntu Server 7.04"
date: 2007-06-20
forum: Installation &amp; Upgrades
---

### Post by rearviewmirror on 2007-06-20
This is a pretty simple request, I've built an Ubuntu 7.04 shell/BBS server.  I wanted to put a fortune in the motd but for some reason "fortunes" will not install using apt-get.

[dildog@ipt-util-21:~] $ sudo apt-get install fortunes
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

[COLOR="Red"][B]The following packages have unmet dependencies:
  fortunes: Depends: fortune-mod (>= 9708-12) but it is not installable
            Depends: fortunes-min but it is not installable
E: Broken packages[/B][/COLOR]
[dildog@ipt-util-21:~] $

---

### Post by danfluidmind on 2007-07-26
It's been a month since you wrote this, so I hope you figureed  this out already. But in case you didn't, one possible problem is that you might not have the "universe" repository in your apt-get list. Use aptitude to see if the package is there.

---

