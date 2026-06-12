---
title: "PLF REPOSITORY for EDGY"
date: 2007-01-05
forum: Installation &amp; Upgrades
---

### Post by useResa on 2007-01-05
Hi,
I have been running Edgy for a while now and basically trouble free.
However, comparing the Dapper sources.list I used to have with the current Edgy sources.list, I noticed the following:

In the Dapper sources.list I had the following repository
> 
## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free
deb-src [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free


Does any one know if there is an Edgy equivalent of these repositories?
Do I just alter *dapper* into *edgy*?

Don't want my installation to break, so to better be safe than sorry I thought I pop up the question first.

---

### Post by userundefine on 2007-01-05
The Edgy repos are:
> ## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy free
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy non-free

---

### Post by useResa on 2007-01-05
Thank you, added this information to my sources.list

I only still had to use the command as described in [ this thread](http://www.ubuntuforums.org/showthread.php?t=318519) to get around the following message
> The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

---

### Post by bapoumba on 2007-01-05
Hello, just for information, plf is not offering ubuntu packages anymore. medibuntu has been set up by a group of french people and currently the packages are being reviewed by a MOTU. The current packages are the same as the former ones from plf, with new version numbers.
[http://medibuntu.sos-sts.com/fr/index.php]("http://medibuntu.sos-sts.com/fr/index.php")
For now, it's in french, so I made an english post in here :
[http://bapoumba.free.fr/?p=13]("http://bapoumba.free.fr/?p=13")

---

### Post by useResa on 2007-01-05
Thank you for this additional information.
Very clear explanation.

---

