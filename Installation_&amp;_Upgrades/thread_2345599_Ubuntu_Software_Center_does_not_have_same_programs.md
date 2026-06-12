---
title: "Ubuntu Software Center does not have same programs 16.04.1"
date: 2016-12-06
forum: Installation &amp; Upgrades
---

### Post by budd2020 on 2016-12-06
I just installed a new hard drive and decided I would start fresh and install ubuntu 16.04.1 LTS. Upon completion of the installation I wanted to install programs I had used on Ubuntu 14.04 LTS but in the software center of 16.04.1 I could only find a few of the programs I had on 14.04. Why are they still available in the software center of 14.04, but I cannot find them for download in 16.04.1?

---

### Post by TheFu on 2016-12-06
Welcome to the forums.

Software Center is an end-user tool with ease of use as the primary goal.  To see **all** the available packages, use almost any other interface to the package management - synaptic, apt, apt-get, aptitude.

However, some old programs just don't have a project team maintaining them anymore, so they cannot be included in newer releases.  As libraries are updated over time which impact these un-maintained projects, the programs cannot be built easily. If automatic builds fail and a human is required to make the port, and nobody steps up to do it, they get dropped.  After all, there are over 30,000 packages available in the Canonical repos, so keeping unpopular programs maintained just isn't possible.

OTOH, you are free to grab the latest code, latest versions of the dependencies and build it for yourself. We'd all appreciate it if you shared that work through a PPA, so others could benefit too. ;)  Perhaps someone else is doing that already. Have you searched for them in a PPA? You could get lucky.

---

