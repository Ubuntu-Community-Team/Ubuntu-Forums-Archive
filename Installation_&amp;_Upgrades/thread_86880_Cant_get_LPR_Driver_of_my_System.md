---
title: "Cant get LPR Driver of my System"
date: 2005-11-06
forum: Installation &amp; Upgrades
---

### Post by Bl@ckD0G on 2005-11-06
Hi everybody, I am a bloody Linux Nub!

I have Ubuntu Breezy 5.10.

I tried to install this ( [http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html](http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html) ) Brother driver.
But the installation crashed right at the beginning.
with the following msg:
```

dpkg -i --force-all hl1470nlpr-1.1.2-1.i386.deb
Selecting previously deselected package hl1470nlpr.
(Reading database ... 103894 files and directories currently installed.)
Preparing to replace hl1470nlpr 1.1.2-1 (using hl1470nlpr-1.1.2-1.i386.deb) ...
Unpacking replacement hl1470nlpr ...
/var/lib/dpkg/info/hl1470nlpr.postrm: line 3: /etc/init.d/lpd: No such file or directory
dpkg: warning - old post-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/postrm: line 3: /etc/init.d/lpd: No such file or directory
dpkg: error processing hl1470nlpr-1.1.2-1.i386.deb (--install):
 subprocess new post-removal script returned error exit status 127
/var/lib/dpkg/tmp.ci/postrm: line 3: /etc/init.d/lpd: No such file or directory
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 hl1470nlpr-1.1.2-1.i386.deb

```

Then i found out that my printer is supported natively by Ubuntu. I installed it (System -> Administration -> Printing) and the printer works fine! So i thought whatsoever, keep the lpr-stuff on the machine.

But now i cant get  anything installed. Whenever i open the Synaptic Packet Manager I receive the following error:
```

E: The package hl1470nlpr needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

```

So i tried:
```

 sudo dpkg -r hl1470nlpr

but...

dpkg: error processing hl1470nlpr (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 hl1470nlpr

```

I dont know what to do? Any Ideas?
Thanks alot!
Greetings

---

