---
title: "Laptop Ubuntu reinstall, overwrite OS"
date: 2007-03-02
forum: Installation &amp; Upgrades
---

### Post by nimy on 2007-03-02
I spent a large part of today trying to upgrade Breezy Badger on my Dell Latitude laptop to Edgy,
but I already was experiencing some bugs and never upgraded this laptop to Dapper Drake etc so I wasn't surprised when I got errors.  I've backed up my home directory and at this point the simplest thing to do would be to download the Edgy ISO and do a new install.  However I'd have to fdisk this machine first, since install CDs don't usually re-partition drives.  I'm not quite sure how to proceed with that however - on my full-size computers I just slap another disk in and fdisk the second.  I'd be happy to try out a network install if that's easier, but I'd need detailed instructions because I've never tried it.  Let me know what you recommend (with links), thanks!

---

### Post by gtratter on 2007-03-02
The live cd *.iso has *gparted* on it. Simply boot your system from the live CD, hit install, either chose manual or automatic partition and you are in business.
You said you had your /home backed up, so all you need when you partition is:
/
/tmp
/home

---

### Post by nimy on 2007-03-03
Thanks!  What a relief!  I'm downloading the ISO now and should have Edgy up and running tomorrow some time...will post results to close this out, but I expect all will be ok :)

---

### Post by nimy on 2007-03-04
As expected, I've reinstalled with no problems and all is well again, thanks :)

---

### Post by gtratter on 2007-03-04
Hooray for **nimy** :guitar:

---

