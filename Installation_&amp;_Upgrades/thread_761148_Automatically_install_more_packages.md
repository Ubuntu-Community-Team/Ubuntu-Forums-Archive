---
title: "Automatically install more packages"
date: 2008-04-20
forum: Installation &amp; Upgrades
---

### Post by songuke on 2008-04-20
Hi all, 
Suppose that I want a fresh installation that comes with some additional packages (that does not ship with Ubuntu, and I do not want to apt-get them from the remote site), since this distribution must serve for a number of different PCs of which network is not available. Are there any methods for this?

Thanks in advance.

---

### Post by erginemr on 2008-04-21
There are two methods developed for this:
1- **Remastersys**: This package allows you to wrap up an installed system, which has been customized with extra packages, to a custom Ubuntu Live CD.
[http://www.remastersys.klikit.org/](http://www.remastersys.klikit.org/)
[http://linuxmint.com/wiki/index.php/Remastersys](http://linuxmint.com/wiki/index.php/Remastersys)

2- **AptOnCD**: This package creates a software repository on a CDROM with custom packages to act as a software repository on freshly installed Ubuntu systems with no Internet access.
[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

In your case, I would take a look at AptOnCD. But use Remastersys instead, by installing an Ubuntu system on a spare machine, customizing it and using Remastersys to recreate a Live DVD (as it is not likely to fit into a CD with extra packages this time) seems to be the best way for you to go. Then comes the question whether all machines have a DVD-ROM drive, but that's a start anyway.

---

