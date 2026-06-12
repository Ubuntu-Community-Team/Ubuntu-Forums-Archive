---
title: "Hardy: Adept  stuck- Can't confirm EULA during install"
date: 2008-09-25
forum: Installation &amp; Upgrades
---

### Post by mibadt on 2008-09-25
Hi,
I downloaded the non-free Google Earth from within Adept into my Kubuntu Hardy. After it fully downloaded, installation got stuck in the 15% stage.  Pressing "Show Details" revealed it's waiting for my approval of the EULA. I've tried every key combination I could think of, yet couldn't enlighten the OK "button" at the bottom of EULA.

I'm on KDE 4.1 if that matters.
Please advise how can I proceed?

Thanks

Michael Badt

---

### Post by soxs on 2008-09-25
Type the following into a console```
sudo apt-get install googleearth-4.3 googleearth-4.3-data
```
You can now accept the license via <enter> and switch the focus with <tab>

Edit:
in case you don't have medibuntu repositories enabled, use this to install debian packages: ```
sudo dpkg -i /path/to/deb/googeearth_something-arch.deb
```
<Note: always install "*-data" packages first

---

### Post by mibadt on 2008-09-25
Thanks for the offer,
I've tried it and got the following errors:

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

I'm afraid if I touch the lock file I'll mess up further ADept operation.
Any idea?

Regards,

Michael Badt

---

### Post by soxs on 2008-09-25
> **mibadt said:**
> Thanks for the offer,
I've tried it and got the following errors:

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

I'm afraid if I touch the lock file I'll mess up further ADept operation.
Any idea?

Regards,

Michael Badt
Try:
```
sudo apt-get install -f
```
this "should" fix it, if not, you still have the option to do it manually within console window and aptitude, in case you know which program messed it up: ```
sudo aptitude
```

---

