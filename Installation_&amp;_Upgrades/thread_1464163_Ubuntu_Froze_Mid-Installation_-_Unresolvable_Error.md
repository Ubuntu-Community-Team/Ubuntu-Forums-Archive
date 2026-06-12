---
title: "Ubuntu Froze Mid-Installation - Unresolvable Errors"
date: 2010-04-27
forum: Installation &amp; Upgrades
---

### Post by wiseguy12851 on 2010-04-27
I was installing several software on a fresh copy of Ubuntu, Ubuntu locked up and froze completely processor and hardware doing nothing. Mouse moved but responded in no way with any clicks. I waited 30 minutes and finally forced the computer off and back on, everything started normally with no errors. After starting synaptic package manager - as expected - it reported corrupt installation so I used the script it gave me to configure and repair, So far simple.

Now the problem lies in several packages which will not repair, remove, clean remove, or re-install. The same errors, over and over. I do not know how to fix Linux Errors and have little experience with Linux in general. I'm a software engineer who grew up with Windows and trying to transition to the world of Linux.

The exact error message differs by package, I don't know how to pull up all the packages but this is the one that applies to **libboost-system** when I try to re-install it

libboost-filesystem1.38.0: subprocess installed post-removal script returned error exit status 2

Any ideas on how to clean these errors up.

---

### Post by mockingbird on 2010-04-27
Try the 600mb alternate install ISO.

---

### Post by tommcd on 2011-01-05
> **wiseguy12851 said:**
> 
Now the problem lies in several packages which will not repair, remove, clean remove, or re-install. The same errors, over and over. ...
Open a terminal and run:
```

sudo apt-get update
sudo apt-get dist-upgrade

```
And post the output here in CODE tags (click the # icon at the top of the window when you post back) so it is easier to read.
FYI: If you have added any third party repos to your sources.list (this includes those all too often problematic PPA repos) then this would be a *very good time* to remove them.

---

