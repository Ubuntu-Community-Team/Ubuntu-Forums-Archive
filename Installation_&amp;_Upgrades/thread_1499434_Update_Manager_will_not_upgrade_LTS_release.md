---
title: "Update Manager will not upgrade LTS release"
date: 2010-06-01
forum: Installation &amp; Upgrades
---

### Post by gnoel on 2010-06-01
Currently running: *8.04 LTS*
Synaptic Package Mgr Release Upgrade option: *Long term support releases only*

Update Manager proposes 11 package updates, but it _does not detect the release upgrade_.  When I change the Release Upgrade option in Synaptic to *Normal releases* and restart the Update Manager, it proposes updating to 8.10 :confused:

I have also tried switching Ubuntu software sources from *Main Server* to *Server for United States* to no avail.

How can I upgrade to 10.4 LTS??  I'm guessing that if I try running do-release-upgrade from Terminal that I will get 8.10, which I do not want.

What am I overlooking??  Thanks for helping!

---

### Post by alfredo.marchini on 2010-06-03
Hi,
I have the same problem here,
I have a pc with 8.04 lts installed, I would like to upgrade it to 10.04 but update manager and do-release-upgrade don't feel the new distribution...

---

### Post by alfredo.marchini on 2010-06-03
hey...
I found the solution...
from terminal run:

update-manager -d

And all it's ok!!!
bye

---

### Post by dino99 on 2010-06-03
[https://help.ubuntu.com/community/LucidUpgrades](https://help.ubuntu.com/community/LucidUpgrades)

---

### Post by gnoel on 2010-06-04
Running update-manager with the -d switch worked, 10.04 LTS is now available.  Thanks, Alfredo.

Does this mean that 10.04 LTS is still marked as a development version?

Anyway, no worries, all is good.

---

### Post by Rytron on 2011-05-14
Will upgrading Ubuntu via 'Update Manager' keep my installed software? Or would it behave just like updating with using an ISO burned onto a CD? I have separate root and home folders.

---

### Post by ottosykora on 2011-05-14
> **Rytron said:**
> Will upgrading Ubuntu via 'Update Manager' keep my installed software? Or would it behave just like updating with using an ISO burned onto a CD? I have separate root and home folders.

it will keep all as it is, but it may install some new versions of this and that. So you may have then new firefox version etc.
But it will not make anything to your settings and data etc.

---

### Post by Rytron on 2011-05-14
> **ottosykora said:**
> it will keep all as it is, but it may install some new versions of this and that. So you may have then new firefox version etc.
But it will not make anything to your settings and data etc.

Thank you ottosykora. So upgrading via Update Manager has this advantage over burning an ISO!

---

### Post by Rytron on 2011-05-15
Would my backed up system files e.g. [COLOR="Indigo"]sudo cp /etc/hosts /etc/**hosts_default**[/COLOR] remain if I ran Upgrade via Update Manager?

---

