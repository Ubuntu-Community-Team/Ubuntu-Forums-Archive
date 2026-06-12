---
title: "Help!! Installed bad package!!"
date: 2007-07-07
forum: Installation &amp; Upgrades
---

### Post by Luft on 2007-07-07
It's kind of a long story but basically I switched my wife's PC from Suse 10.0 to Ubuntu 7.04.  One of the packages she uses is Gramps.  So we installed Gramps.  However it failed to read the older version of the database from Suse.

I figured that maybe I could install the older version on my laptop, read the file and export it to a GEDCOM file which the new version could read.  I couldn't find the older version in a deb file so I installed ailien and used that to convert the older Suse RPM file to a deb file.  I used the switch to include scripts.

I tried to install the deb file onto my laptop but there were errors.  Now it won't let me uninstall it (it tells me that there are major problems with the install and I should reinstall before uninstalling.)  I can't install an upgrade, I can't seem to --force anything.

I'm stuck!! :(

---

### Post by bapoumba on 2007-07-07
Could you please paste the errors when you try to purge it (not just remove)?

---

### Post by Luft on 2007-07-07
This is what I get when I try to purge:

eric@MobileTux:~$ sudo apt-get --purge remove gramps
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  gramps*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking, 10.3MB disk space will be freed.
Do you want to continue [Y/n]? Y
dpkg: error processing gramps (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 gramps
E: Sub-process /usr/bin/dpkg returned an error code (

---

