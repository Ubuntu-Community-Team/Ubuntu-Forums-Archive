---
title: "is upgrading from cd possible?"
date: 2007-03-14
forum: Installation &amp; Upgrades
---

### Post by oomisilekootsi on 2007-03-14
Hi, I've been using ubuntu 5.10.  I would like to upgrade to the LTS version but I only have a dialup connection.  Is there a way to upgrade from the cd without wiping out the contents of my harddrive?

---

### Post by Kateikyoushi on 2007-03-14
You can upgrade from the alternate CD, or you could move your /home to it's own directory then you can keep your settings even if you reinstall. [LINK]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by oomisilekootsi on 2007-03-15
Thanks for the info.  If I follow the steps described, would I lose the additional softwares and drivers that I installed on my present Ubuntu version? (For example, the Lucent modem driver, Qcad, etc.)

---

### Post by az on 2007-03-15
WHen you upgrade from the cd, you will only be upgrading the packages that are part of the base install.  So pretty much anything that is not from the main repository will not be upgraded (because it is not there).

That means that those packages will either
1.  Continue to work fine.  This is the case if they do not depend on any specific version of the core packages.
2.  Be removed by the package manager.  This is the case if they depend on a specific version of a package that is going to be removed or upgraded.
3.  Stay installed but not work anymore.  This can be the case if your software was installed "by hand" without using the package manager, or if it was installed by the package manager, but the package is not properly built ( this can be the case with many third-part applications)

As far as your modem driver, you have it installed and running on your current kernel.  You will get a newer kernel installed as part of the upgrade.  You can always recompile the driver for your new kernel, but since this is a binary-only driver, there is a chance that it will not work with the new kernel (it would probably work, if it was open source...)

You may be able to still use your old kernel, though.  I don't remember if you can use a Breezy kernel with Dapper.

---

### Post by oomisilekootsi on 2007-03-16
Thanks a lot. I think I would try upgrading via the alternate install cd.  BTW, where can I get this cd?  Is this cd included in the free cd package ordered from shipit? (My order is comming in a few days..)

---

### Post by Kateikyoushi on 2007-03-16
I could not find info about it in shipit but from answers in the forum seems the alternate cd does not come with the shipit package.
So you should download it for yourself, select a mirror and scroll down till you see the alternate CD. [LINK]("http://www.ubuntu.com/GetUbuntu/downloadmirrors")

---

### Post by oomisilekootsi on 2007-03-16
The alternate-install cds on the list are for version 6.10.  I think I need to upgrade to 6.06 first before I can upgrade to 6.10.

---

### Post by oomisilekootsi on 2007-03-16
Ahhh, I've found it.  ... Now the painstaking task of downloading the file through dialup connection...
     Thanks a lot.

---

### Post by linear on 2007-03-16
Someone has done a nice job of obscuring the location of the Dapper alternate install images. :rolleyes:

In most mirrors, you can replace "edgy" with "dapper" in the path to get to the right place. (EDIT: As you've found.)

For example: [http://mirror.cc.columbia.edu/pub/linux/ubuntu/releases/dapper/](http://mirror.cc.columbia.edu/pub/linux/ubuntu/releases/dapper/)

---

