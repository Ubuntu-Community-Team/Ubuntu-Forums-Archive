---
title: "Needing help with updating 6.06 to 6.10 (Beginner)"
date: 2008-03-07
forum: Installation &amp; Upgrades
---

### Post by John4300 on 2008-03-07
Hello there, few hours ago I "Found" out my old computer with Ubuntu running it. And not having much exprience, runned to error quickly.

I saw this computer is running ubuntu 6.06 - Wich is old dist. So, I found out help updating this to 6.10 (And up) from help.ubuntu.com, ran command (gksu "update-manager -c") in my terminal and started uptading with Update Manager... After a while though, the "Preparing for Update" window did not move, and few minutes later, this popped out.

"Failed to fetch [http://packages.freecontrib.org/plf/dists/dapper/Release.gpg](http://packages.freecontrib.org/plf/dists/dapper/Release.gpg) Could not connect to packages.freecontrib.org:80 (34.52.53.34), connection timed out"

I'm connected to internet and I think this should go just fine, but I have no idea why this have popped up and what to do in order to continue. Should I get 6.10 somewhere else? Should I directly upgrade to 7.10 somehow? Should I put in 7.10 CD and install it?

Thanks for your help.
-John4300

---

### Post by taurus on 2008-03-07
You need to edit /etc/apt/sources.list

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```
and put a #  in front of that repo to comment it out.

```
**[COLOR="Blue"]#[/COLOR]**http://packages.freecontrib.org/
```
Save it and close down gedit window.  Now, see if you can upgrade again.

---

