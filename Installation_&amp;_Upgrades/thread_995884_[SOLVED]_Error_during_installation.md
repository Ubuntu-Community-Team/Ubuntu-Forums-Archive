---
title: "[SOLVED] Error during installation"
date: 2008-11-28
forum: Installation &amp; Upgrades
---

### Post by MikeAnix on 2008-11-28
[FONT="Arial"]I've been trying to install either 8.04 or 8.10 with no success.  However, 7.10 used to run fine.

Pentium III, 933 Mhz.  Ubuntu install on the entire 60 Gig hard drive.  Upgrading from 7.10 to 8.04 did not work, so I tried to reinstall from scratch.  No luck either.

Using the GIU, I got all sort of error messages saying that CD drive might be dirty, hard disk faulty, etc.  I did the usual checks.

CD drives are OK
CD has been check.  No issue.
Check hard drive, no issue.  Replace with another one just in case, but still no luck.

Using the Alternate CD to install, it went OK for some time, then stopped working at the Install Software stage (always stopped at 6%).  I looked at the syslog for errors.  Below is a pasting of the faulty lines.  

Any help will be greatly appreciated, since I've been spending numerous hours so far to have this PC running.

Thanks[/FONT]

> Nov 28 03:16:37 in-target: dpkgÂ*: erreur de traitement de /cdrom//pool/main/g/gegl/libgegl-0.0-0_0.0.18-1_i386.deb (--unpack)Â*:

Nov 28 03:16:37 in-target:  files list file for package `libgsf-1-114' is missing final newline

Nov 28 03:16:37 in-target: Des erreurs ont Ã©tÃ© rencontrÃ©es pendant l'exÃ©cutionÂ*:

Nov 28 03:16:37 in-target:  /cdrom//pool/main/g/gegl/libgegl-0.0-0_0.0.18-1_i386.deb

Nov 28 03:16:37 in-target: L'exÃ©cution a Ã©tÃ© arrÃªtÃ©e car il y avait trop d'erreurs.

Nov 28 03:16:37 in-target: E: Sub-process /usr/bin/dpkg returned an error code (1)

Nov 28 03:16:37 in-target: tasksel: erreur du programme aptitude (100)

Nov 28 03:16:38 kernel: [ 3943.135904] ISO 9660 Extensions: Microsoft Joliet Level 3

Nov 28 03:16:38 kernel: [ 3943.178628] ISO 9660 Extensions: RRIP_1991A

Nov 28 03:16:39 kernel: [ 3943.362579] ISO 9660 Extensions: Microsoft Joliet Level 3

Nov 28 03:16:39 kernel: [ 3943.405343] ISO 9660 Extensions: RRIP_1991A

Nov 28 03:16:39 main-menu[2671]: WARNING **: Configuring 'pkgsel' failed with error code 1

Nov 28 03:16:39 main-menu[2671]: WARNING **: Menu item 'pkgsel' failed.

Nov 28 03:16:43 main-menu[2671]: INFO: Modifying debconf priority limit from 'high' to 'medium'

Nov 28 03:16:43 debconf: Setting debconf/priority to medium

Nov 28 03:16:43 main-menu[2671]: DEBUG: resolver (libnewt0.52): package doesn't exist (ignored)

Nov 28 03:16:43 main-menu[2671]: DEBUG: resolver (efi-modules): package doesn't exist (ignored)

Nov 28 03:16:43 main-menu[2671]: INFO: Falling back to the package description for console-setup-udeb

Nov 28 03:16:57 main-menu[2671]: INFO: Falling back to the package description for console-setup-udeb

Nov 28 03:16:57 main-menu[2671]: INFO: Menu item 'save-logs' selected

---

### Post by taurus on 2008-11-28
How fast did you burn the ISO image to a CD?

---

### Post by MikeAnix on 2008-11-28
> **taurus said:**
> How fast did you burn the ISO image to a CD?

I can't tell, but I used the same CDs to install on different PCs without any problem.  I also did an integrity check of the CD, and no problems were found.

Furthermore, the fact that I can't even update from 7.10 to 8.04 using the update manager kind of suggest that the CD is not the problem.

I will try burning at a slower speed (I have nothing to lose at this point) and post the result later.

Thanks

---

### Post by MikeAnix on 2008-12-11
Problem solved.

I'm posting an answer to my own post to help people that might be having the same problem.

The nature of my problem had to do with the memory banks.  I had 512 Megs of RAM, which all passed with success the memory test.  The configuration was 128+256+128.  

I re-arranged the configuration to 128+128+256, and Intrepid Ipex goes like a charm.

Hope this may help someone else.

---

