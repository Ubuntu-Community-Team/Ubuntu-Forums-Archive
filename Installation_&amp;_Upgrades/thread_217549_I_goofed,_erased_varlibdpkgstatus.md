---
title: "I goofed, erased /var/lib/dpkg/status"
date: 2006-07-17
forum: Installation &amp; Upgrades
---

### Post by jamaas on 2006-07-17
I managed to fix a bunch of things ...
but now get this, is there an easy way to correct this?  I get if for about 40 packages!  :-(

Thanks

Jim

dpkg: serious warning: files list file for package `oclock' missing, assuming package has no files currently inst alled.

dpkg: serious warning: files list file for package `libstdc++5-3.3-dev' missing, assuming package has no files cu rrently installed.

dpkg: serious warning: files list file for package `lsof' missing, assuming package has no files currently instal led.

dpkg: serious warning: files list file for package `python2.4-soappy' missing, assuming package has no files curr ently installed.

---

### Post by ajgreeny on 2006-07-17
I think if you just make a list of the packages listed as currently having no files installed, and reinstall the packages, this should probably put things right.  You may need to make a new empty plain text file called *status* and put it into  */var/lib/dpkg* or just rename the *status.old* (I have such a file on my system) and see what happens.

Is it just for the 40 or so packages you get this message, and is that the approx number that you think you've installed?  My files of that name are pretty big (1.2Mb each) but if you have only installed a few packages (40) with apt-get or synaptic, then they will be prety small files anyway.

---

