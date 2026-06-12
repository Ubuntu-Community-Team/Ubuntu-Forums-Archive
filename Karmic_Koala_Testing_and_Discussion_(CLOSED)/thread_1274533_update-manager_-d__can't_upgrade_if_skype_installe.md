---
title: "update-manager -d  can't upgrade if skype installed"
date: 2009-09-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Andre-D on 2009-09-24
I click "update" (to 9.10) and it says downloading "1" then "2 of 2"  - than I enter password.
Then it just closes (ends)

here's the log:
```

andre@Loke:~$ update-manager -d
extracting 'karmic.tar.gz'
authenticate 'karmic.tar.gz' against 'karmic.tar.gz.gpg' 
/var/lib/python-support/python2.6/dbus/connection.py:242: DeprecationWarning: object.__init__() takes no parameters
  super(Connection, self).__init__(*args, **kwargs)
can't load DistUpgradeViewGtk (__init__() takes exactly 3 arguments (2 given))
can't load DistUpgradeViewKDE (No module named PyQt4.QtCore)

Reading cache

Checking package manager
Reading package lists: Done
Reading state information: Done
Reading state information: Done
Reading state information: Done
Done downloading            
Reading package lists: Done
Reading state information: Done
Reading state information: Done
Reading state information: Done

Updating repository information
Done http://archive.ubuntu.com karmic Release.gpg
Ignored http://archive.ubuntu.com karmic/main Translation-en_US
Failed http://archive.ubuntu.com karmic/main Translation-en_US
Done http://archive.ubuntu.com karmic Release
Done http://archive.ubuntu.com karmic Release
Done http://archive.ubuntu.com karmic/main Packages
Done http://archive.ubuntu.com karmic/main Packages
Done downloading            

Checking package manager
Reading package lists: Donearmic/main Packages: 65  
Reading state information: Done
Reading state information: Done
Reading state information: Done

Calculating the changes

Could not calculate the upgrade 

An unresolvable problem occurred while calculating the upgrade: 
The package 'skype' is marked for removal but it is in the removal 
blacklist. 

This can be caused by: 
* Upgrading to a pre-release version of Ubuntu 
* Running the current pre-release version of Ubuntu 
* Unofficial software packages not provided by Ubuntu 

If none of this applies, then please report this bug against the 
'update-manager' package and include the files in 
/var/log/dist-upgrade/ in the bug report. 


Restoring original system state

Aborting
Reading package lists: Done
Reading state information: Done
Reading state information: Done
Reading state information: Done
andre@Loke:~$ 


```

Removed Skype - then it works ... it would be wise to do something about it :)

---

