---
title: "Adept_Manager database locked"
date: 2007-01-12
forum: Installation &amp; Upgrades
---

### Post by coughlin on 2007-01-12
During a Java JRE install there was a Java requirement for the user to 'ok' the Java license.  Adept package manager was stuck with no way for me to click 'ok' during the Adept installation.

When I closed Adept, I could not re-open Adept without it throwing a dialog box, saying 

"Read only mode ... Database locked ... Adept Manager"
... and that there is an existing Adept (or Apt etc.) process running.

Despite quitting Adept Package Manager and re-booting, I can't get Adept Manager to work, anymore.  I've already tried killing any Adept or Apt processes.

?

/Mike

---

### Post by pebo on 2007-01-12
I'm not familiar with adept but assuming it works the same way as Synaptic this might help:

```
sudo rm /var/cache/apt/archives/lock
```

Edit: there is another lock file: /var/lib/dpkg/lock - you might have to remove this as well!

---

### Post by coughlin on 2007-01-12
thanks - for the hint, Pebo; but, after removing both 'lock' files, Adept_Manager database is still locked upon opening Adept_Manager.

If I can't find a way to unlock this Adept_Manager database, I can't install/un-install any packages ... and my Linux installation is screwed.  I'll have to hose it ... and re-start ... NOT very confidence inspiring ... i.e. the idea that if one stumbles upon a faulty apt package, it could ruin your whole Linux installation!

---

### Post by coughlin on 2007-01-12
Ahhh ... the following un-locked the Adept_Manager database ... for resumed, normal use ...

```
sudo dpkg --configure -a
```

thanks ...

---

### Post by jrcmuniz on 2007-06-06
Same problem here... and now solved!
You're the man... THANKS!!!!!!
Cheers
Joao.

---

### Post by Kissack on 2007-06-24
and sorted my problem too (neded to configure a previous package that itself needed a file correcting)

thanks

---

### Post by valdiney on 2007-12-23
Thank you Guy. You saved me too!

---

