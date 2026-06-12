---
title: "Wine is hell"
date: 2006-12-07
forum: Installation &amp; Upgrades
---

### Post by osprey_criminal on 2006-12-07
I'm trying desperately to get WINE to do anything relative to progress.

This is my most current error.

 
sudo apt-get update
...
...
W: GPG error: [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


any ideas?

---

### Post by 23meg on 2006-12-07
Make sure you aren't running another package manager (such as Synaptic or the update manager) while installing.

---

### Post by osprey_criminal on 2006-12-07
omg...hehe...thanks

---

### Post by osprey_criminal on 2006-12-07
new error


libGL warning: 3D driver claims to not support visual 0x5b
libGL warning: 3D driver claims to not support visual 0x5b
libGL warning: 3D driver claims to not support visual 0x5b




?

---

### Post by 23meg on 2006-12-07
Do you get this when you're trying to run something with WINE? If so what exactly?

---

