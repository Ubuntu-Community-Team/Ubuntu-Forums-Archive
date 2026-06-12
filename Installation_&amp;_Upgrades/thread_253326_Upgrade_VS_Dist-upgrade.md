---
title: "Upgrade VS Dist-upgrade"
date: 2006-09-08
forum: Installation &amp; Upgrades
---

### Post by Frunktz on 2006-09-08
Hi!
I read that is better do ONLY dist-upgrade when I update my distro (it can be only days or only new (K)Ubuntu release).
So what's the difference between those two command?
And why sometime people use aptitude instead apt-get?
I've read that aptitute UNINSTALL dipendence not used. only that difference?

Thanks a lot and sorry for my bad bad English

---

### Post by viciouslime on 2006-09-08
Dist-upgrade checks to see if ther are new dependencies on packages wjere as upgrade simply checks for new versions of packages. So, say for example the ubuntu team decided they wanted banshee in the default install, they would add banshee as a dependency of the ubuntu-desktop package, but if you just did an upgrade apt-get wouldn't bother to check whether any new dependencies had been added to ubuntu-desktop, it would just look for packages whose version numbers have changed. I think that's it anyway. So, you should use dist-upgrade to upgrade from say dapper to edgy, or if you are using edgy at the moment while it is still being developed you should also use dist-upgrade because they may add things to the ubuntu-desktop package among others.

Otherwise, a standard upgrade will simply keep your system up to date with the latest security fixes or critical bug fixes that get released.

As for aptitude, I believe you have correctly identified the only difference... though I may be wrong.

---

### Post by Frunktz on 2006-09-08
Ok for security fixes, so generally is the same thing do a dist-upgrade also for bugfix? However on the topic regar Breezy->Dapper I read that run upgrade then dist-upgrade broke your distro.

---

### Post by az on 2006-09-08
apt-get update will update all packages that can be updated without causing some packages to be removed.  For example, if a new version of a package starts to conflict with another package, it will not be installed, because upgrading should not remove packages.

Dist-upgrade enforces all packages to be updated, and will remove packages that newly conflict.

There was a bug which caused the ubuntu-desktop package to be removed in some cases.

You can dist upgrade, and then manually re-install ubuntu-desktop (or check to see if it is still there) to be sure.  The best way to go from Breezy to Dapper is to use the update-notifier.  Update your breezy ssytem and you will get notified that a new version of ubuntu is available.  

Click the button to upgrade to the new version and everything will work out - it will figure out what to do to keep Ubuntu-desktop installed.

Apt-get and aptitude use the same dependencies (they are built into the package - you cannot change them!) Aptitude will keep track of what packages were installed and will help you remove no-longer-needed packages when you remove the package that brought in those dependencies to begin with.

Most people use Apt-get (or synaptic).

---

### Post by Frunktz on 2006-09-08
Ja, I know the difference between upgrade and dist-upgrade, but I don't know why can break the entire system. Now I know that's only a bug in the old ubuntu version. Right?

Thanks :)

---

