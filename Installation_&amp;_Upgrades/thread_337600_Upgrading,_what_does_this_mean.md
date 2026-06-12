---
title: "Upgrading, what does this mean?"
date: 2007-01-13
forum: Installation &amp; Upgrades
---

### Post by The Pinny Parlour on 2007-01-13
Hi,

I am trying to upgrade from dapper to edgy and get this error:

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://www.getautomatix.com/apt/dists/dapper/main/binary-i386/Packages.bz2:](http://www.getautomatix.com/apt/dists/dapper/main/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)
[http://www.getautomatix.com/apt/dists/dapper/main/binary-i386/Packages.bz2:](http://www.getautomatix.com/apt/dists/dapper/main/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)
[http://xgl.compiz.info/dists/dapper/main/binary-i386/Packages.gz:](http://xgl.compiz.info/dists/dapper/main/binary-i386/Packages.gz:) 404 Not Found
[http://xgl.compiz.info/dists/dapper/aiglx/binary-i386/Packages.gz:](http://xgl.compiz.info/dists/dapper/aiglx/binary-i386/Packages.gz:) 404 Not Found


Any help would be great.

Thanks,
RESOLVED:  removed the lines from sources.list

---

### Post by The Pinny Parlour on 2007-01-13
I also get:

Cannot install all available updates

Some updates require the removal of further software. Use the function "Mark All Upgrades" of the package manager "Synaptic" or run "sudo apt-get dist-upgrade" in a terminal to update your system completely.

The following updates will be skipped:
dpkg-dev
libc6-dev

---

### Post by hal10000 on 2007-01-13
@The Pinny Parlour:

Just do what it tells you to do. Either start synaptic and use "Mark All Upgrades", or in case you don't have synaptic installed, open a terminal window and type
[COLOR="Red"]sudo apt-get update[/COLOR]
[COLOR="Red"]sudo apt-get dist-upgrade[/COLOR] and say yes to the packages that are to be upgraded.

---

### Post by The Pinny Parlour on 2007-01-13
Hi,

Thanks for the reply.  I get the following:

~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


I'm not sure what is going on.  I try what is recommended: 
```
gksu "update-manager -c"
```
and I only get so far then errors happen.  

Think I will have to just do a fresh install as the upgrade path is full of errors for me.

---

### Post by The Pinny Parlour on 2007-01-13
UPDATE: I think the upgrade is actually starting to work.

---

### Post by hal10000 on 2007-01-13
you have to use BOTH red colored commands from my posting above.

btw, synaptic is better than update-manager.

---

