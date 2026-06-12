---
title: "Updates"
date: 2012-04-27
forum: Installation &amp; Upgrades
---

### Post by Bolshy on 2012-04-27
Hi,
Having just installed ubuntu 12.04 64bit I started the updates of which I think most came down but then I got this error
Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/pt.archive.ubuntu.com_ubuntu_dists_precise_universe_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

When opening package manager I get this message

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/pt.archive.ubuntu.com_ubuntu_dists_precise_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.   

I have tried several times to send an error report but that doesn't work either can anybody help?
Thanks in advance ;-)

---

### Post by kc1di on 2012-04-27
Try the following in a terminal

```
sudo rm /var/lib/apt/lists/* -vf 
sudo apt-get update 
```
copy one line at a time to your terminal and hit enter. 
Then try update again.
Hope it helps 
D ;)

---

### Post by Bolshy on 2012-04-27
Well thanks for that it certainly seems to have worked updates are installing. :-)

---

### Post by kc1di on 2012-04-27
> **Bolshy said:**
> Well thanks for that it certainly seems to have worked updates are installing. :-)

Your welcome Please take the time to mark the thread as solved.
Thanks ;)

---

