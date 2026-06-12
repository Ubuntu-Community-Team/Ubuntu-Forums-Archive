---
title: "Consistency of an Installation"
date: 2012-01-04
forum: Installation &amp; Upgrades
---

### Post by tinybuntu on 2012-01-04
What is Ubuntu's strategy for achieving and maintaining consistent installations?

Scenario: I have two Oneiric installations, both started out with regular 64bit Desktop installations. I manually added a few packages on each of the installations. I don't remember exactly which packages and in which sequence but obviously the set and/or the sequence was different on the two systems in question.

At some point I noticed that some of my shell scripts produced different results on the two systems. Further investigations showed that one system had "gawk" the other one had "mawk" as the default awk.

I did not install any *awk package on either system so awk, mawk, gawk must have been pulled in because other packages had dependencies to awk and it seems that by installing additional packages, probably in different sequences, the systems end up with differently resolved dependencies to very basic functions such as awk.

Can this be avoided? Would it be possible that all packages in the repository that have dependencies to an "awk", resolve those by pulling in exacly **one** version and flavour of awk? Either gawk or mawk but not both and not in an non deterministic way.

In fact, talking about "mawk", which seems to be the default, even in 11.10 I got a pretty old version: 1.2, dated Dec, 22, 1994 which definitely has known bugs in clamping unsigned integers to signed integers. The bug appears to be fixed since years but not in V1.2

And while I am at it: Is there a way to after the facts investigate exactly which of the installed packages pulled in mawk and which pulled in gawk? At least I would want to know what I would break on one of the two systems if I did a "[FONT="Courier New"]update-alternatives --config awk[/FONT]" and set that to the same awk on both systems

---

### Post by 2F4U on 2012-01-04
To put it plain, it is your responsibility as system administrator to make sure both systems are setup equally, if that is needed by you. Ubuntu (and no Linux system I know of) can do that for you. Different applications have different dependencies and you hit Y in both cases. To make it clear, not Ubuntu installed something on your machine, you told it to install something on your machine.

---

### Post by Mark Phelps on 2012-01-04
> **tinybuntu said:**
> What is Ubuntu's strategy for achieving and maintaining consistent installations?

Don't know if you'd actually call it a "strategy", but their "approach" for achieving consistent installations is providing a standard image for doing such installations.  If you get the install images all from the same place, they will all have the same contents.

As to "maintaining", there is no way that Canonical could possibly to that, since you are free to add/change/remove anything you want after the initial install.

I know how this is done in the commercial world (at least, in my experience) and that is through a combination of (1) using only authorized pre-built OS images for installation, and (2) locking down the resulting PCs so that only authorized folks can make changes.  Canonical has already done (1) -- but there is no way they can do (2).

---

### Post by tinybuntu on 2012-01-05
> **2F4U said:**
> To put it plain, it is your responsibility as system administrator to make sure both systems are setup equally, if that is needed by you. Ubuntu (and no Linux system I know of) can do that for you. Different applications have different dependencies and you hit Y in both cases. To make it clear, not Ubuntu installed something on your machine, you told it to install something on your machine.

I agree with you to a very large degree, still, in the given example it would be conceivable to me that all packages made available by a specific distribution, if they have dependencies to an "awk" they could pull in exactly one and the same awk and not differnt ones.

Let's say I am a developer and want to devlop an application that runs on Ubuntu systems. On what foundation can I depend on? Again, in this example, do I have to live with the fact that some installations invoke mawk when I say awk, and others invoke gawk if I say awk?

---

### Post by 2F4U on 2012-01-06
The choice of what awk will be used is up to the developer. Those different awk versions certainly have slightly different functionality and the developer will choose the version that provides the functionality he needs for his application. The developer has the freedom of choice. 
There is not much a distribution like Ubuntu can do about it except for pulling in all the different versions into the repository. If Ubuntu would want to restrict the distribution to exactly one awk, they would have to either leave out all applications that use other versions or they would have to fork any application that uses a different version. This would be a huge effort.

---

### Post by tinybuntu on 2012-01-06
> **2F4U said:**
> The choice of what awk will be used is up to the developer. Those different awk versions certainly have slightly different functionality and the developer will choose the version that provides the functionality he needs for his application. The developer has the freedom of choice. 
There is not much a distribution like Ubuntu can do about it except for pulling in all the different versions into the repository. If Ubuntu would want to restrict the distribution to exactly one awk, they would have to either leave out all applications that use other versions or they would have to fork any application that uses a different version. This would be a huge effort.

Thank you for your insight. So the message in this scenario would be, as an application developer who needs awk, don't just invoke it as "awk" because it might resolve to different executables via /etc/alternatives, call the one you need explicitly via /usr/bin/gawk or /usr/bin/mawk and of course specify a dependency in your package that pulls in the variant you need at install time. The only downside this might have is that pulling in gawk or mawk via dependency resolution also modifies the /etc/alternatives and by doing so it might break other packages which depend on a specific variant but imply that their required variant is actually mapped to /usr/bin/awk via /etc/alternatives. Inevitably this means to be on the safe side you bypass the /etc/alternatives mechanism entirely.

Many of us have seen similar effects by "/bin/sh" being directly linked to /bin/dash

---

