---
title: "Problem with the clock, reinstalated ubuntu"
date: 2008-08-14
forum: Installation &amp; Upgrades
---

### Post by eastir on 2008-08-14
Hi, i have a partition with /home and another one for /. Yesterday, i reinstalled Ubuntu 8.04 (32 bits) maintain the partition /home. 

My problem is that when i select, in the clock, other places for the time and the weather (click in configure in other cities), ubuntu says:

 
"No se pudo establecer la zona horaria del sistema" - "It was not possible to establish the hourly zone for the system"

"Message did not receive a reply (timeout by message bus)"

And, the hour don't change.
For example, i have in my configuration, Granada (where i live), Madrid, and London (Canada, where i am now), and only i can select madrid or granada (both have the same hours) but London, with other hour i can't.

thanks for your help

---

### Post by Pumalite on 2008-08-14
Are you wired to the Internet during installation?

---

### Post by eastir on 2008-08-14
yes

---

### Post by Pumalite on 2008-08-14
Burn a new CD. Do md5sum on the iso, burn at 4x or less. Check CD integrity before install

---

### Post by cariboo on 2008-08-14
Sometimes reinstallaing is not a universal fix all. That is the Widows way of doing things. Have you tried:

```
sudo dpkg-reconfigure tzdata
```

Jim

---

### Post by Pumalite on 2008-08-14
It could be a bad burn too.

---

