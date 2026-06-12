---
title: "Browser Crashes and Upgrade Manager gives error"
date: 2010-05-06
forum: Installation &amp; Upgrades
---

### Post by bo_n_tulsa on 2010-05-06
After upgrading to 10.04, I noticed Firefox would suddenly crash for no apparent reason.  
I tried to run the update manager to see if there were updates available.  There were a whole slew of them.  They downloaded and began installing, but it gave me an error.  
Clicking the "do not enter" warning icon gives me this:

```
Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Problem parsing dependency Depends, E:Error occurred while processing postfix (NewVersion1), E:Problem with MergeList /var/lib/dpkg/status, E:The package lists or status file could not be parsed or opened.'
```

Anybody have an idea how I can fix this and install the updates?

Also, synaptic gives me this error when opening:
> 
E: Problem parsing dependency Depends
E: Error occurred while processing postfix (NewVersion1)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

thx

---

### Post by quixote on 2010-05-07
Have you already tried in Synaptic: Edit > Fix Broken Packages?  That doesn't usually do much, but it's worth a try.  If that either doesn't find anything or doesn't fix it, open a terminal (Applications > Accessories > Terminal) and type```
sudo dpkg --configure -a
``` More info about dpkg than you want can be found by typing in a terminal ```
man dpkg
```  
After that try the upgrade again:```
sudo apt-get update   *(to get the most recent repository info)*
sudo apt-get upgrade
``` Then reboot, just to make sure all the fixes "take."

Hopefully, that'll deal with it.  If not, let us know what went wrong.

---

