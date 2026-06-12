---
title: "dpkg was interupted - Help please!"
date: 2008-08-30
forum: Installation &amp; Upgrades
---

### Post by smoky on 2008-08-30
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

This is what happens when I try to use Update Manager and when I try to add programs to my system.

I am not a super user, nor an advanced user, so be kind when explaining how I go about fixing this problem please, and remember that if you help me with this it is learning on my behalf and isn't that how we all learn?

smoky

---

### Post by kellemes on 2008-08-30
Open a terminal window and start typing..
```
sudo dpkg --configure -a
```
enter your password when asked.

---

### Post by smoky on 2008-08-30
Hi Kellemes

Thanks for that, it fixed one problem, now it brings up another:

[B]You have 5 broken packages on your system!

Use the "Broken" filter to locate them.[/B]

I hope your patient and don't mind sorting through this mess. I have two systems with Ubuntu on them, one is Edubuntu and this with Ubuntu 8.04 (this one is having problems but Edu is fine).

Cheers

---

### Post by kellemes on 2008-08-30
Again from a terminal window..
```
sudo apt-get install -f
```

---

