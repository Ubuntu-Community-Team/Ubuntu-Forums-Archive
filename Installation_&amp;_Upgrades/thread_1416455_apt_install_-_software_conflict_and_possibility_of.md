---
title: "apt install - software conflict and possibility of FORCE install?"
date: 2010-02-26
forum: Installation &amp; Upgrades
---

### Post by pushkarajthorat on 2010-02-26
Hello Everybody,

I've used RedHat distro, in those distors I could install *all* the packages with NO package conflicting other, everything was installed and worked correctly. 

I got familiar with Ubuntu/Debian from last 6 months and used apt(synaptic) for installing the softwares, I noticed if a software conflicts other, it uninstalls the conflicting software, if both the softwares work fine on other distro in my openion it should also work on Ubuntu too. 

I wonder if I could FORCE install a software even if it conflicts.

Please bear with me, may be this could be very naive for you guys.

Regards,
Pushkaraj

---

### Post by Kakers on 2010-02-26
Try this:

apt-get install -y --force-yes <package(s)>

---

### Post by pushkarajthorat on 2010-02-27
> **Kakers said:**
> Try this:

apt-get install -y --force-yes <package(s)>

Kakers, Thanks for your reply, it worked, but I still wonder if this will still work for *all* the softwares, keeping my fingures corossed.

---

