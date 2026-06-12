---
title: "dpkg/apt hang during upgrade of lvm2"
date: 2008-11-05
forum: Installation &amp; Upgrades
---

### Post by haxwithaxe on 2008-11-05
Hey all,
Just upgraded to 8.10(stable) from 8.04 on my desktop.  Upgrading the packages the next day and I get to "Backing up any LVM2 metadata that may exist..." and it stays that way.  How long does it stay that way?  I let it sit over night and didn't get back to it until after I got back from school (12-16hrs), it's still there.  The computer isn't frozen I can do any thing I want except install/remove packages.  I killed synaptic and tried "apt-get -f install", failed said to try "dpkg --configure -a" same result as when upgrading.  Went hunting for a fix. Found [http://irclogs.ubuntu.com/2008/01/17/%23xubuntu.txt](http://irclogs.ubuntu.com/2008/01/17/%23xubuntu.txt).  Tried various dpkg commands including the ones listed in the irc log above. 
dpkg
          --clear-selections
          --purge lvm2
          --force-remove lvm2
          --force-remove-essential lvm2
apt-get --purge remove lvm2
All either failed with errors or hung the same way as the original.
Any help would be appreciated.  Thanks.

hax  (;_;)

---

