---
title: "Anyone heard when 17.10 (desktop) is going to be available again?"
date: 2017-12-26
forum: Installation &amp; Upgrades
---

### Post by rbmorse on 2017-12-26
Santa dropped parts for a new machine under the tree.  I'd really like to put 17.10 on it instead of an older release, but if it is going to be awhile I'll just do an interim install of 16.04 and send it on to production for upgrade at a later date.

---

### Post by ubfan1 on 2017-12-27
The [http://releases.ubuntu.com/17.10/](http://releases.ubuntu.com/17.10/) is still active, but hasn't been updated as far as I can see, so I'd avoid it.  If you can't use 16.04 on the new machine, maybe adding the   kernel parameter  modprobe.blacklist=intel-spi  would allow a safe install, and then in the /etc/modprobe.d/blacklist file, add the line
 install module_name /bin/false   to prevent it from being added in by anthing else, but you risk damaging your machine, I make no guarantees those fixes will work or are complete, and recommend you wait until some official fix comes out.  Then again, what BIOS are you using?  I have a Phoenix and ran 17.10 without problems.  Insyde definitely has the problem.

---

### Post by QIII on 2017-12-27
I'd avoid 17.10 like the plague at this point.  Canonical messed up badly by getting tangled up in the Lenovo BIOS mess.   Both Lenovo and Canonical have a share in the fiasco and they both have some explaining to do.  Unless Canonical can demonstrate very clearly that the issue is fixed, my opinion is that they should kill 17.10.

Just my two cents.

---

### Post by mörgæs on 2017-12-27
It's highly unlikely that it will be killed. 
It's highly likely that we will see a fixed 17.10.1-ISO for download. The kernel is fixed so the only thing we need is a respin and some tests. 

Still this problem could reoccur in the future as hardware vendors think they have a right to store more and more... let's call it unexpected functions in UEFI.

---

