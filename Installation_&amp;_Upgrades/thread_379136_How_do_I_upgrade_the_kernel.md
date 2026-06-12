---
title: "How do I upgrade the kernel?"
date: 2007-03-08
forum: Installation &amp; Upgrades
---

### Post by skywatcher on 2007-03-08
I'm still new to Ubuntu and Linux, so please excuse what may seem like stupid questions.

I use Ubuntu 6.06 and the kernel version is 2.6.15-28-386. How do I find out if there is a newer version, and if there is, how do I install it?

---

### Post by Kateikyoushi on 2007-03-08
Th update manager will tell you or synaptic. If you prefer terminal then

```
sudo aptitude update
sudo aptitude dist-upgrade
```

It will display packages can be upgraded, if a kernel upgrade is avaible that wil be among them.

---

### Post by skywatcher on 2007-03-08
Thanks, Kateikyoushi!

---

### Post by skywatcher on 2007-03-08
Is 2.6.15-28-386 the latest version? Synaptic doesn't show anything later than this.

---

