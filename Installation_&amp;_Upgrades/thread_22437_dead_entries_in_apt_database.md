---
title: "dead entries in apt database?"
date: 2005-03-27
forum: Installation &amp; Upgrades
---

### Post by vaskark on 2005-03-27
I've got some entries in my apt database that are empty and I'd like to remove them but synaptic doesn't seem to allow me to. Is there a command line option for this? These apps are no longer on my system yet they still exist in the database.

Thanks.

---

### Post by Xian on 2005-03-27
Does the right-click on package > Mark for Complete Removal option not accomplish this?

---

### Post by vaskark on 2005-03-28
[QUOTE=Xian]Does the right-click on package > Mark for Complete Removal option not accomplish this?[/QUOTE]

Unfortunately not. It's greyed out. This whole mess happened because I was using checkinstall to build my own debs, and when they failed to install these entries got put in the database anyway :cry:. I'm hoping for a nifty CL solution, I guess -- something I can run that will check the entire database and recognize these dead entries and delete them.

---

### Post by garion on 2005-07-27
Same problem here, trying to install an older version of wine from source with checkinstall... the deb package was generated but failed to install... and left me with a dead entry in apt-get database.  Does anyone know where the database is stored in the system, and how to go about changing it, undoing what checkinstall did?

---

### Post by garion on 2005-07-27
I fiddled with this problem a little... and seems like the only place that got messed up by a failed checkinstall run was /var/lib/dpkg/available and /var/lib/dpkg/status... just changed that... and seems to be okay.

---

