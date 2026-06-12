---
title: "Package Manager?"
date: 2011-04-27
forum: Installation &amp; Upgrades
---

### Post by nightwarrior51 on 2011-04-27
I opened up the Synaptic Package Manager and I got this ```
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

```

What do I do?

---

### Post by nightwarrior51 on 2011-04-27
Nvm, I'm an idiot

---

### Post by KegHead on 2011-04-27
Hi!

In your terminal;

sudo apt-get update

sudo dpkg --configure -a

KegHead

---

### Post by Blasphemist on 2011-04-27
If following the instruction in the message doesn't fix it, run synaptic package manager, edit menu, fix broken packages.

---

