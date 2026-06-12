---
title: "Cannot calculate upgrade error"
date: 2010-04-08
forum: Installation &amp; Upgrades
---

### Post by keithclark on 2010-04-08
I'm getting the following when trying to upgrade from 10.04 Beta1 to Beta2:

Could not calculate the upgrade

An unresolvable problem occurred while calculating the upgrade:
The package 'ubuntu-desktop' is marked for removal but it is in the removal blacklist.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

Not sure how to resolve.

Keith

---

### Post by emanuel.b on 2010-04-08
Probably because upgrading from pre-release to pre-release version is unsupported. You'll just have to wait until the normal version comes out...

---

### Post by keithclark on 2010-04-08
> **emanuel.b said:**
> Probably because upgrading from pre-release to pre-release version is unsupported. You'll just have to wait until the normal version comes out...

Of course it is supported.  I've been doing it fine since the first Alpha.  It is how I got to Beta1

Keith

---

### Post by emanuel.b on 2010-04-08
Hmm, perhaps you're right ](*,). Well, maybe it just a bug in the repos. If so, they should work it out in a few days. Otherwise it's just a bug in the system. (That much is to be expected from running a beta.)

---

### Post by keithclark on 2010-04-08
> **emanuel.b said:**
> Hmm, perhaps you're right ](*,). Well, maybe it just a bug in the repos. If so, they should work it out in a few days. Otherwise it's just a bug in the system. (That much is to be expected from running a beta.)

Oh yeah, all part of the Beta testing fun.  I was just hoping it was something that I could correct easily.

Keith

---

### Post by appier on 2010-04-30
Any suggestions on how to resolve this error?  I am getting this same error, only I am attempting to upgrade to 10.04 LTS.  This is the official, stable release.--Mark

---

### Post by johnny1978 on 2010-05-03
I'm getting the same error. I have unselected the packages not supported by ubuntu just in case, but no luck. I'm upgrading from 9.10 to 10.4 LTS.
Should I report this as a system bug, or is it a repository bug?

This is what appears when I sudo do-release-upgrade

johnny@johnny-laptop:~$ sudo do-release-upgrade
[sudo] password for johnny: 
Checking for a new ubuntu release
Done Upgrade tool signature
Done Upgrade tool
Done downloading            
extracting 'lucid.tar.gz'
authenticate 'lucid.tar.gz' against 'lucid.tar.gz.gpg' 
tar: Removing leading `/' from member names

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
WARNING: Failed to read mirror file
Done downloading            

Checking package manager
Reading package lists: Doneucid-backports/universe Packages: 94    
Reading state information: Done
Reading state information: Done
Reading state information: Done

Calculating the changes

Calculating the changes

Could not calculate the upgrade 

An unresolvable problem occurred while calculating the upgrade: 
The package 'ubuntu-desktop' is marked for removal but it is in the 
removal blacklist. 

This can be caused by: 
* Upgrading to a pre-release version of Ubuntu 
* Running the current pre-release version of Ubuntu 
* Unofficial software packages not provided by Ubuntu 

If none of this applies, then please report this bug against the 
'update-manager' package and include the files in 
/var/log/dist-upgrade/ in the bug report. 


Restoring original system state

Aborting
Reading package lists: Donearmic-backports/universe Packages: 94    
Reading state information: Done
Reading state information: Done
Reading state information: Done

---

### Post by appier on 2010-05-03
I gave up and did a fresh install on the two machines which were both giving me this error.  On the Dell Precision 370, fresh install was perfect--just worked, right out of the box.  On the Dell Optiplex GX260, the fresh install is having some problems with the xorg driver for the Intel i845, but that is not the fault of the installer.

---

### Post by hawthornso23 on 2010-05-10
This bug is hitting everyone who has installed an alternative desktop. (In my case xubuntu-desktop). The workaround seems to be to uninstall other desktops first - then upgrade - then reinstall the other desktops.

This bug has been reported by a bunchaton of people and there are numberous duplicates on launchpad. It is well understood and it doesn't look like fixing it would be hard. However it is still unassigned, or even marked invalid in many duplicates. Looks like nobody feels like bothering to fix it. Until somebody does I can't be bothered upgrading.

---

