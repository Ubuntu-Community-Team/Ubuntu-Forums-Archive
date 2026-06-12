---
title: "Problem installing updates"
date: 2010-04-01
forum: Installation &amp; Upgrades
---

### Post by stevehoenstine on 2010-04-01
I'm new to Ubuntu.  After I got the OS up and running (v9.10), I was prompted to download and install some updates.  The download is complete, but when I try to install the updates, I receive the following message.  What should I do?

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by bigsmitty64 on 2010-04-01
well it says to run 
```
sudo dpkg --configure -a
```

maybe try that in terminal, but wait for someone else to confirm first. :)

---

### Post by bigsmitty64 on 2010-04-01
OR go into system/administration synaptic package manager  then edit/fix broken packages

---

### Post by stevehoenstine on 2010-04-01
Thanks.  I tried the sudo dpkg command in the terminal, but kept getting more errors.  But then I tried updating in the package manager.  Doing that seems to have cleared up all of my problems.  Thanks!

---

### Post by bigsmitty64 on 2010-04-01
Glad to help. And welcome to the forums.

---

