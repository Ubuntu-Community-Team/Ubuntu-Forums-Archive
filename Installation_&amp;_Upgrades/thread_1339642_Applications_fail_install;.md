---
title: "Applications fail install;"
date: 2009-11-27
forum: Installation &amp; Upgrades
---

### Post by WASHAD on 2009-11-27
I've recently installed Ubuntu 9.10. Since doing so, no application will completely install. Bellow is the error that I get. Strangely, though, the application does seem to run even after the reported failure. 





> installArchives() failed: Selecting previously deselected package libaudio2.

(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 143476 files and directories currently installed.)

Unpacking libaudio2 (from .../libaudio2_1.9.2-1_amd64.deb) ...

Selecting previously deselected package acm.

Unpacking acm (from .../acm_5.0-25ubuntu2_amd64.deb) ...

Processing triggers for desktop-file-utils ...

Processing triggers for man-db ...

Setting up bcmwl-kernel-source (5.10.91.9+bdcom-0ubuntu4) ...

dpkg (subprocess): unable to execute installed post-installation script: Exec format error

dpkg: error processing bcmwl-kernel-source (--configure):

 subprocess installed post-installation script returned error exit status 2

Setting up libaudio2 (1.9.2-1) ...



Setting up acm (5.0-25ubuntu2) ...



Processing triggers for libc-bin ...

ldconfig deferred processing now taking place

Errors were encountered while processing:

 bcmwl-kernel-source


---

### Post by lemming465 on 2009-11-29
You appear to have at least one incompletely configured package.  The first thing I'd try is some command line package maintenance:```
sudo -i
aptitude clean
aptitude update
aptitude full-upgrade -f
```
If that doesn't do it, do you have any karmic-incompatible 3rd party repositories enabled in your software sources?

---

### Post by WASHAD on 2009-12-01
Thank you for the reply. To be honest, I've tried installing 9.10 several times (different discs, different distros) and each time it has been buggy like this.

I finally resorted back to 9.04 and everything is happy again. 

SteveJ

---

### Post by lemming465 on 2009-12-01
Hmmm, my first answer was too generic.  More specifically, it's having trouble with > dpkg: error processing bcmwl-kernel-source (--configure):

Broadcom (wireless?) chips are not very well supported yet by Linux, alas.  Lean on your vendor to use chips with open source drivers, and on broadcom to cooperate on making one.  In the meantime you pretty much at the mercy of the vendor; if and when they get around to supporting an OS upgrade, you can move.

I used to have similar trauma with an Atheros wireless chip in a Toshiba laptop that spends most of its time with my daughter (running windows).  Fortunately, in the last two years the open-source Atheros drivers have gotton a lot better.  I'm keeping my fingers crossed on the Broadcom front.

If you aren't actually compiling your own kernels, and whatever binary support the 9.10 kernel shipped with is actually operating your hardware, you might be able to dispense with the bcmwl-kernel-source package.  I'm not sure if that was being pulled in explicity by you or implicitly by the DKMS (Dell-inspired dynamic kernel module support) stuff.  Implicitly is possible, if Broadcom is shipping binary drivers with a source glue layer, as Nvidia does.  In which case I'd guess the broadcom chip wasn't working under 9.10.  Dunno if that's wireless or wired ethernet in your case, I'm assuming it's one of them.

Jaunty Jackalope is supported for another year yet, so unless you need to live on the bleeding edge, you can put off upgrading for a while, as you have done, and see if 10.04 or 10.10 is any better.  However, ff this is the only problem you are having with 9.10, and if all the hardware you actually care about is working, the configuration error with the one package is in that case fairly innocuous.  As you have found, it won't generally keep other things from proceeding normally.

If you have a launchpad account, or are willing to set one up, you could use *apport-bug bcmwl-kernel-source* to report your issue from a 9.10 install (if you have a spare partition you are willing to put it on).

---

### Post by WASHAD on 2009-12-05
Thanks for the response Lemming465. I'm back to 9.04 now and everything is working well again. I think I'll take your advice and wait for a while. 

SteveJ

---

