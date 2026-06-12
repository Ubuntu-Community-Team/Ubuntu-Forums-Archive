---
title: "xlispstat package"
date: 2006-10-31
forum: Installation &amp; Upgrades
---

### Post by lucascr on 2006-10-31
Dear all,
I used to install xlispstat, an object-oriented environment for statistical computing and dynamic graphics. It is not in the repository, but I have an old deb package for Debian with the last version (which is 3 years old, but it is the latest version...). 
If I try to install it, I get a problem with xlib missing library. By the way, it installs and runs fine, but it is marked as broken by synaptic (and then automatically removed).

I noted that an already installed package libx11-6 says "This package provides the main client interface to the X Window System, and is otherwise known as 'Xlib'".
Thus, if I correct understand, it seems I have the required library, except is named differently and does not satisfy the dependency. 
How can I fix this, or otherwise get a xlispstat deb package for Ubuntu?
Thanks,

Luca

---

### Post by lucascr on 2006-11-02
Solved installing xlispstat_3.52.18-1.1_i386.deb for breezy available via [http://packages.ubuntulinux.org](http://packages.ubuntulinux.org)

Luca

---

