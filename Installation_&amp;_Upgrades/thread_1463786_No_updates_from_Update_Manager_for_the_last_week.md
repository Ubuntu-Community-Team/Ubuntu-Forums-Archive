---
title: "No updates from Update Manager for the last week"
date: 2010-04-27
forum: Installation &amp; Upgrades
---

### Post by SA@ on 2010-04-27
Hi All, My Ubuntu 9.10's update-manager has not shown any updates since I last updated on April 17th. I looked at the security updates released since 4/17 and I do not have the related packages installed (as far as I can tell). 
 
Is this normal? I usually get some packages to be updated every week.
 
I also ran apt-get update;apt-get upgrade which did not show any packages to be updated.
 
I have also tried changing package sources in "System|Administration|Software Sources"/"Download From" 
 
 
Thanks in advance
SA@

---

### Post by zvacet on 2010-04-28
Updates doesn't come in some regular time frame,but as far I can remember there was updates few days ago.

```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get dist-upgrade
```

---

### Post by tommcd on 2010-04-28
> **SA@ said:**
> 
Is this normal? I usually get some packages to be updated every week.
I have been using (and abusing!!) Ubuntu since the first release (Ubuntu 4.10). The usual pattern is that there are a lot of frequent updates after a new version is released. The updates then gradually diminish in frequency as the next version of Ubuntu looms on the horizon. (In this case Ubuntu 10.04 LTS is only 1 day away).
> **SA@ said:**
> 
I also ran apt-get update;apt-get upgrade which did not show any packages to be updated.
 
I always use:
```

sudo apt-get update
sudo apt-get dist-upgrade

```
There are occasional cases where a *new* package needs to be installed, or an old package has it's name changed or whatever. In these cases, "apt-get upgrade" will hold back these packages; but "apt-get dist-upgrade" will upgrade those packages.
Note that using the Ubuntu GUI update manager is simply a GUI front end to running 
"sudo apt-get dist-upgrade".
If "apt-get dist-upgrade" still show no updates, then I would be satisfied with that.

---

### Post by SA@ on 2010-04-28
Thanks much! I will try the dist-upgrade method

> **tommcd said:**
> I have been using (and abusing!!) Ubuntu since the first release (Ubuntu 4.10). The usual pattern is that there are a lot of frequent updates after a new version is released. The updates then gradually diminish in frequency as the next version of Ubuntu looms on the horizon. (In this case Ubuntu 10.04 LTS is only 1 day away).

I always use:
```

sudo apt-get update
sudo apt-get dist-upgrade

```There are occasional cases where a *new* package needs to be installed, or an old package has it's name changed or whatever. In these cases, "apt-get upgrade" will hold back these packages; but "apt-get dist-upgrade" will upgrade those packages.
Note that using the Ubuntu GUI update manager is simply a GUI front end to running 
"sudo apt-get dist-upgrade".
If "apt-get dist-upgrade" still show no updates, then I would be satisfied with that.

---

