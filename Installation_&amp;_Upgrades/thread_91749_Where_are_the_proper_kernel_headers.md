---
title: "Where are the *proper* kernel headers?"
date: 2005-11-17
forum: Installation &amp; Upgrades
---

### Post by p0ltergeist on 2005-11-17
After installing kubuntu, I've attempted to install fglrx drivers, and it's attempting to custom-compile a module into the kernel. But there's a problem: /usr/src is empty.
There are kernel headers in /usr/include/linux  but the problem is that these are the headers for 2.6.11 and doing a cat /proc/version returns the following line:
Linux version 2.6.12-9-386 (buildd@rothera) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Oct 10 13:14:36 BST 2005

I've taken a long look through synaptic, and only found kernel-souces-2.6.11
fglrx won't install properly unless it has the souces for the kernel currently being run on my system.

And I have to ask why the 2.6.11 headers are on the system when 2.6.12-9-386 is the kernel installed? :confused:

---

### Post by leezer3 on 2005-11-18
Hiya,
Sounds to me as if you need to enable the extra repositories from the repositories menu (You should have all of these enabled).
Then do a search for **linux-headers** and it should find them for you. Alternatively, you can install the **linux-source** package, which will give you the complete kernel source, which is occasionally needed. (Not in your case though :D )

Cheers

-Leezer-

---

### Post by Freddy on 2005-11-18
Yes, do enable the extra repositories. unmark the mirrors in sources.list.
```
sudo kate /etc/apt/sources.list
```
You need to download an install the linux-restricted-modules in "Base System (restricted)" for your kernel and processor.   /// Freddan

---

