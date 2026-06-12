---
title: "Cupsys"
date: 2007-12-20
forum: Installation &amp; Upgrades
---

### Post by speedy6 on 2007-12-20
When I update using the update manager I always get the error:
E: /var/cache/apt/archives/cupsys_1.3.2-1ubuntu7.2_i386.deb: subproces pre-installation script gaf een foutwaarde 1 terug

Last sentence in eglisch: script gave faultvalue 1 back.
What Can I do about it?

Thanks

---

### Post by speedy6 on 2007-12-24
anyone?

---

### Post by pointone on 2007-12-24
Try:

```
sudo apt-get clean
```

...and try again.

---

### Post by speedy6 on 2007-12-25
Still the same error.
See screen shot.
I hope you know another solution...

---

### Post by speedy6 on 2008-01-07
> **speedy6 said:**
> Still the same error.
See screen shot.
I hope you know another solution...

Anyone?

---

### Post by Seisen on 2008-01-07
Open up a terminal and go to /var/cache/apt/archives/ 

```
cd /var/cache/apt/archives/  
``` the type this in the terminal

```
sudo rm -i cupsys_1.3.2-1ubuntu7.2_i386.deb 
``` this will delete the cupsys.deb file. Then ```
sudo apt-get update
``` and then you shouldn't have any errors.

---

### Post by speedy6 on 2008-01-07
No still the same error.
After you're commands I got 6 updates witch succeeded but the cupsys still not.
Another idea?

---

### Post by speedy6 on 2008-01-10
other idea's?

---

