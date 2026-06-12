---
title: "Synaptic Package Manager Problem"
date: 2008-05-05
forum: Installation &amp; Upgrades
---

### Post by redserpent7 on 2008-05-05
I've been using Ubuntu for two days now, today I've started my computer and tried to install Google Earth. I got this Error Message upon installation.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I've tried the command and also got the same error that dpkg won't start, I've tried to start Synaptic Package Manager from System->Administration but I got the same error.

So how can I fix this problem without having to reinstall Ubuntu from scratch.?

Please Help?????

---

### Post by Oldsoldier2003 on 2008-05-05
> **redserpent7 said:**
> I've been using Ubuntu for two days now, today I've started my computer and tried to install Google Earth. I got this Error Message upon installation.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I've tried the command and also got the same error that dpkg won't start, I've tried to start Synaptic Package Manager from System->Administration but I got the same error.

So how can I fix this problem without having to reinstall Ubuntu from scratch.?

Please Help?????
```
sudo dpkg --configure -a
```

---

### Post by redserpent7 on 2008-05-05
> **Oldsoldier2003 said:**
> ```
sudo dpkg --configure -a
```

Thanx worked for me... Sun Java was a broken Package so I guess that was the problem there.... Thx again, it appears that I'm still a n00b here :(

---

### Post by xardas on 2008-05-05
Yeah but what if the "dpkg --configure -a" doesn't work either. What then? I'm getting the message:

Setting up python-central (0.6.5ubuntu1) ...
pycentral: pycentral pkginstall: package terminator is not installed
pycentral pkginstall: package terminator is not installed
pycentral: pycentral pkginstall: package terminator is not installed
pycentral pkginstall: package terminator is not installed
dpkg: error processing python-central (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of displayconfig-gtk:
 displayconfig-gtk depends on python-central (>= 0.6.1); however:
  Package python-central is not configured yet.
..................................................
dpkg: too many errors, stopping
dpkg: ../../src/packages.c:252: process_queue: Assertion `!queuelen' failed.
Aborted (core dumped)

How can I get the package manager to work again in this scenario?

---

### Post by menachem on 2008-05-08
> **xardas said:**
> Yeah but what if the "dpkg --configure -a" doesn't work either. What then? I'm getting the message:

Setting up python-central (0.6.5ubuntu1) ...
pycentral: pycentral pkginstall: package terminator is not installed
pycentral pkginstall: package terminator is not installed
pycentral: pycentral pkginstall: package terminator is not installed
pycentral pkginstall: package terminator is not installed
dpkg: error processing python-central (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of displayconfig-gtk:
 displayconfig-gtk depends on python-central (>= 0.6.1); however:
  Package python-central is not configured yet.
..................................................
dpkg: too many errors, stopping
dpkg: ../../src/packages.c:252: process_queue: Assertion `!queuelen' failed.
Aborted (core dumped)

How can I get the package manager to work again in this scenario?

try

```
sudo dpkg --configure -a --force-all
```

you can see more information on what I did to solve this [here]("http://ubuntuforums.org/showthread.php?t=779996&highlight=Python-central")

---

### Post by stankopp on 2008-05-08
What do I do if SPM doesn't start at all? There are no messages.  It just doesn't start.

---

### Post by stankopp on 2008-05-08
My problem has been solved.  It was actually an "unable to resolve host" issue.

---

