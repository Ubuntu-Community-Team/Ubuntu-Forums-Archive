---
title: "Zoneminder apt-get Problem"
date: 2007-02-11
forum: Installation &amp; Upgrades
---

### Post by fjseymour on 2007-02-11
I had a Zoneminder install fail.  Now I can do nothing with apt-get or Synaptic.  They both fail with the following message: 
"fjseymour@ubuntu-desktop:~$ sudo apt-get -m upgrade
Reading package lists... Done
Building dependency tree... Done
E: The package zoneminder needs to be reinstalled, but I can't find an archive for it.

The original insall attempt was from a downloaded .deb package for Zoneminder that I ran from my "home/Download" directory as sudo
What other logs do you need to see?  Any help is appreciated.

Rick

---

### Post by bapoumba on 2007-02-12
Hello,
try removing it with dpkg: **sudo dpkg --purge zoneminder**
See **man dpkg** to use --force option or stronger actions.

---

### Post by mmoalem on 2007-02-14
hi there - have the same problem... purge, force-reinstall and install didnt work... did you manage to clean it?
cheers
michel

---

### Post by fjseymour on 2007-02-18
Problem fixed.  Thank you for the suggestion Bapoumba, but I had no luck with that as Zoneminder had things to messed up to delete.  Soooo, out I noticed a upgraded version of Zoneminder (1.22.3-2), downloaded the .deb for Dapper to my Download directory and it (re) installed without problems. 

Once the install was done, I was able to uninstall it with no problems, Synaptic and Apt-Get were both happy & everything was back to normal.

Thanks for the attempt.

Rick

---

### Post by bapoumba on 2007-02-18
Congratulations, and thanks for posting your workaround :)

---

