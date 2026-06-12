---
title: "update-manager show everything up to date, but there are upgradeable packages"
date: 2014-07-23
forum: Installation &amp; Upgrades
---

### Post by el_baby on 2014-07-23
Hi,

I did a fresh installation of 14.04 and today I noticed that even when synaptic shows that there are a bunch of packages to upgrade, I run update-manager and, after checking sources it says that everything is up to date.

Is update-manager ignoring some packages?

Is this something new in 14.04?

Or something is wrong somewhere?

[ATTACH=CONFIG]254959[/ATTACH]

---

### Post by grahammechanical on 2014-07-23
> [COLOR=#000000]Is update-manager ignoring some packages?[/COLOR]

Holding back is a more accurate term.

> [COLOR=#000000]Is this something new in 14.04?[/COLOR]

No.

> [COLOR=#000000]Or something is wrong somewhere?[/COLOR]

No.

Packages are put in the archive/repositories as and when they are ready. Often they depend on other packages that are not ready. So they are held back. If we used the apt- get commands of update and upgrade we may be shown a list of packages held back. Apt-get may even tell us of packages that have been downloaded and not installed.

There is a small risk that bringing in these held back packages could break something. This is why most users should use Update Manager.

Regards.

---

### Post by el_baby on 2014-07-23
Hi, grahammechanical,

thanx for your reply... this doesn't seem to be the case of held back packages because of unmet dependencies, since if I mark all upgrades in synaptic (which is careful with dependencies, as also is apt-get without the "--force" option) they actually get selected for upgrade (if there were unmet dependencies, synaptic would NOT mark the upgrades and would show a message accordingly... seen that a lot of times).

I just did not upgraded the packages within synaptic just out of curiosity.

---

### Post by Dennis N on 2014-07-23
The update manager (Software Updater) is providing "phased updates".

[http://www.omgubuntu.co.uk/2013/08/phased-updates-to-start-rolling-out-for-ubuntu-13-04](http://www.omgubuntu.co.uk/2013/08/phased-updates-to-start-rolling-out-for-ubuntu-13-04)

But apt-get or Synaptic will offer all updates - they don't use phased updates.

---

### Post by Dennis N on 2014-07-23
I meant to include this for those wanting to know more. A write up with all the details of how phased updates work:

[http://lwn.net/Articles/563966/](http://lwn.net/Articles/563966/)

---

### Post by el_baby on 2014-07-23
Excelent!!

Thanx for your replies, Dennis.

---

