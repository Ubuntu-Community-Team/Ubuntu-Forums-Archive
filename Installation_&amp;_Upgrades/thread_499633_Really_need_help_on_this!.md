---
title: "Really need help on this!"
date: 2007-07-12
forum: Installation &amp; Upgrades
---

### Post by Luft on 2007-07-12
It's kind of a long story but basically I switched my wife's PC from Suse 10.0 to Ubuntu 7.04. One of the packages she uses is Gramps. So we installed Gramps. However it failed to read the older version of the database from Suse.

I figured that maybe I could install the older version on my laptop, read the file and export it to a GEDCOM file which the new version could read. I couldn't find the older version in a deb file so I installed ailien and used that to convert the older Suse RPM file to a deb file. I used the switch to include scripts.

I tried to install the deb file onto my laptop but there were errors. Now it won't let me uninstall it.  When I try to purge it I get:

eric@MobileTux:~$ sudo dpkg --purge gramps
dpkg: error processing gramps (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 gramps

---

### Post by HermanAB on 2007-07-12
Hmm, the lesson of the day is *not* to experiment on an important machine.  If all you have is an important machine, then install the free VMware Server and install experimental system(s) on that.  Yes it is slow, but the peace of mind is priceless.

Anyhoo, when you can't 'uninstall' something, just 'find' it and delete it.  Simple as that:
$ find / -name whatever
$ sudo rm -Rf /wherever/whatever

In Windoze there is a Registry to clean up.  In Linux there isn't.

'Hope that helps!

Herman

---

### Post by Luft on 2007-07-13
I removed the package by hand like you suggested but the error message continue whenever I try to do updates.

---

