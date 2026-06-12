---
title: "Necessary to upgrade from 8.04 Release Candidate?"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by gnigamica on 2008-04-24
I upgraded to the 8.04 release candidate a week or so ago.  I've kept the system updated since then.  Is it necessary to upgrade to the official 8.04 LTS release?  Or has my system updated itself into the current version?

Update Manager shows that the system is up to date.

Thanks.

---

### Post by ibutho on 2008-04-24
Its not necessary if you have kept up with the updates.

---

### Post by gnigamica on 2008-04-24
Thanks.  I'll save the ISO bandwidth for somebody who needs it.

---

### Post by ssj3strife on 2008-04-24
Is there a terminal command I can run to print the name of the current Ubuntu release the system is running? I'd like to check out if it says "Hardy beta" or not, if just for peace of mind. :)

---

### Post by noynac on 2008-04-24
> **ssj3strife said:**
> Is there a terminal command I can run to print the name of the current Ubuntu release the system is running? I'd like to check out if it says "Hardy beta" or not, if just for peace of mind. :)

You can check the installed version as shown below; it doesn't distinguish between beta and final, though. If the update manager doesn't show any updates you have Hardy final.

SYSTEM MONITOR TOOL

system > administration > system monitor > system

COMMAND LINE

cd /etc
cat issue

---

### Post by zvacet on 2008-04-24
```
lsb_release -a
```

---

### Post by kam.samji on 2008-04-24
Thanks for this. It always help to read the forum beofre posting as I was just about to do with this very question! I, too, will now save the bandwitdth for other users/convertees..

Great work guys, thanks a lot.

Kam

---

### Post by ssj3strife on 2008-04-24
Yup! Thank you, gentlemen. :)

---

