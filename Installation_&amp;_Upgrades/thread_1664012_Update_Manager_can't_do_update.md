---
title: "Update Manager can't do update"
date: 2011-01-10
forum: Installation &amp; Upgrades
---

### Post by Rocket J Squirrel on 2011-01-10
Update Manager wants to update a Libreoffice help file. But there is a problem:

```
installArchives() failed: (Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 257058 files and directories currently installed.) 
Preparing to replace libobasis3.3-en-us-help 3.3.0-17 (using .../libobasis3.3-en-us-help_3.3.0-18_i386.deb) ... 
Unpacking replacement libobasis3.3-en-us-help ... 
dpkg: error processing /var/cache/apt/archives/libobasis3.3-en-us-help_3.3.0-18_i386.deb (--unpack): 
 trying to overwrite '/opt/libreoffice/basis3.3/help/en/sdraw.cfg', which is also in package libobasis3.3-en-us-draw 3.3.0-17 
No apport report written because MaxReports is reached already
dpkg-deb: subprocess paste killed by signal (Broken pipe) 
Errors were encountered while processing: 
 /var/cache/apt/archives/libobasis3.3-en-us-help_3.3.0-18_i386.deb
```

Maybe someone has an idea how to overcome this issue?

---

