---
title: "Can't upgrade!!!"
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by yelserpdog on 2007-04-24
Hi all,

WHen I try to upgrade using the upgrade manager it starts to download the packages then comes up with this error

Failed to fetch [http://wine.budgetdedicated.com/apt/dists/edgy/Release](http://wine.budgetdedicated.com/apt/dists/edgy/Release) Unable to find expected entry  main/binary-amd64/Packages in Meta-index file (malformed Release file?)

Anyone know what the problem is? Shoudl I just update using a cd?

---

### Post by Sef on 2007-04-24
If that ([http://wine.budgetdedicated.com/apt/dists/edgy/Release](http://wine.budgetdedicated.com/apt/dists/edgy/Release)) is in your source list, then I would comment it out.  You can comment it out by putting a # before it.  By commenting it out, the machine will not read it. (#[http://wine.budgetdedicated.com/apt/dists/edgy/Release](http://wine.budgetdedicated.com/apt/dists/edgy/Release))  

Applications > Accessories > Terminal

gksudo gedit /etc/apt/sources.list

---

### Post by yelserpdog on 2007-04-24
THanks for that, but I tried this and I'm now getting the following when I type the command you posted

(gedit:6905): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

---

