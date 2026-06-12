---
title: "Update and Upgrade before apt-get optional utilities or after?"
date: 2017-08-13
forum: Installation &amp; Upgrades
---

### Post by walker452 on 2017-08-13
What is considered "Best Practice", update/upgrade just after install and *before* apt-get of 'optional utilities' or update/upgrade *after* apt-get  of 'optional utilities'?

---

### Post by vasa1 on 2017-08-13
What do you mean by "apt-get of 'optional utilities'"?

---

### Post by walker452 on 2017-08-13
> **vasa1 said:**
> What do you mean by "apt-get of 'optional utilities'"?

After I install Ubuntu I may want to install inxi via "apt-get install inxi", or ssh with "apt-get install openssh-server".

---

### Post by vasa1 on 2017-08-13
I'd update, upgrade, then install.

---

### Post by walker452 on 2017-08-13
Sounds reasonable, thanks.

---

### Post by &amp;KyT$0P# on 2017-08-13
Not that you could really do it the other way around.  If you haven't yet run [FONT=Courier New]sudo apt-get update[/FONT] (or equivalent, e.g. update manager) on a newly installed system, it knows only the installed software.  So if you try to do it backwards, it'd tell you your optional utilities don't exist in the repos, even though they actually do.

---

