---
title: "WARNING: Deprecated config file /etc/modprobe.conf"
date: 2012-04-21
forum: Installation &amp; Upgrades
---

### Post by LanceHaverkamp on 2012-04-21
sudo modprobe -a intel-rng
Returns:

WARNING: Deprecated config file /etc/modprobe.conf, all config files belong into /etc/modprobe.d/.

I have no idea what this means as this is way outside what I normally do.  Nothing seems to be happening, I see no intel-rng in either modprobe.conf or modprobe.d 

How do I get this module installed?

---

### Post by Toz on 2012-04-21
The warning message refers to the fact that the use of /etc/modprobe.conf is deprecated - meaning this is the old way of doing things. The "new" way is to create individual files in /etc/modprobe.d for module configuration.

---

### Post by LanceHaverkamp on 2012-04-21
That much I did understand, What it doesn't explain is why modprobe is trying to write to the old location--or what we should be using if modprobe can't handle it.

So returning to the unanswered question: How do I get this module installed?

---

### Post by Toz on 2012-04-22
> **LanceHaverkamp said:**
> That much I did understand, What it doesn't explain is why modprobe is trying to write to the old location--or what we should be using if modprobe can't handle it.

I don't think modprobe is trying to write to that file. I think its reading the existing file and warning you that it is deprecated. What is the contents of /etc/modprobe.conf? If you want to get rid of the warning, just move the contents of that file to /etc/modprobe.d and delete the file.

> So returning to the unanswered question: How do I get this module installed? 
What happens if you:
```
sudo modprobe intel-rng
```
Does it load?
```
lsmod
```

---

