---
title: "Cannot run hp-toolbox"
date: 2011-05-02
forum: Installation &amp; Upgrades
---

### Post by Onesimus on 2011-05-02
I have done a fresh installation of Natty Narwhal on a number of my home PCs.  However, on one of them I have encountered a few problems.

I have installed hplip-gui in order to manage my HP printers.  On the machine I am having problems with I get the following message:

```
user@onesimus:~$ hp-toolbox

HP Linux Imaging and Printing System (ver. 3.11.1)
HP Device Manager ver. 15.0

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

error: Unable to load Qt4 support. Is it installed?
```

The output of hp-check is:
```
user@onesimus:~$ hp-check

HP Linux Imaging and Printing System (ver. 3.11.1)
Dependency/Version Check Utility ver. 14.3

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Note: hp-check can be run in three modes:
1. Compile-time check mode (-c or --compile): Use this mode before compiling the
HPLIP supplied tarball (.tar.gz or .run) to determine if the proper dependencies
are installed to successfully compile HPLIP.                                    
2. Run-time check mode (-r or --run): Use this mode to determine if a distro    
supplied package (.deb, .rpm, etc) or an already built HPLIP supplied tarball   
has the proper dependencies installed to successfully run.                      
3. Both compile- and run-time check mode (-b or --both) (Default): This mode    
will check both of the above cases (both compile- and run-time dependencies).   

Saving output in log file: hp-check.log

Initializing. Please wait...
 
---------------
| SYSTEM INFO |
---------------

Basic system information:
Linux onesimus 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 i686 i386 GNU/Linux

Distribution:
ubuntu 11.04

Checking Python version...
OK, version 2.7.1 installed

Checking PyQt 4.x version...
Traceback (most recent call last):
  File "/usr/bin/hp-check", line 304, in <module>
    from PyQt4 import QtCore
ImportError: /usr/lib/pymodules/python2.7/PyQt4/QtCore.so: undefined symbol: _ZNK13QElapsedTimer6secsToERKS_
```

I am also having problems with running virtualbox, but don't know whether they are related.  Any suggestions would be greatly received.

---

### Post by lechien73 on 2011-05-02
Yes, the problems are likely related. Have you tried installing python-qt4?

```
sudo apt-get install python-qt4
```

If that doesn't work then, you could check to see if anything has broken the QT4 dependencies. For example, I don't know if you're in Belgium, but the Belgian EID card software has been documented to cause this problem in the past:

[http://ubuntuforums.org/showthread.php?t=1560810](http://ubuntuforums.org/showthread.php?t=1560810)

Like the screen name, by the way :) "receive him kindly the way you would me"

---

### Post by Onesimus on 2011-05-02
> **lechien73 said:**
> Yes, the problems are likely related. Have you tried installing python-qt4?

```
sudo apt-get install python-qt4
```


I have tried reinstalling python-qt4 several times, but to no avail.

I have also un-installed virtualbox, kdenlive, hplip-gui.
But upon re-installation the problem persists.

---

### Post by Onesimus on 2011-05-02
Did a total re-install.  Now works

---

