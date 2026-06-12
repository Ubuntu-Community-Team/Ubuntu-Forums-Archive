---
title: "Upgrade to 8.04"
date: 2008-06-19
forum: Installation &amp; Upgrades
---

### Post by 0perator on 2008-06-19
i currently have 7.10

i have the cd for 8.04 and i was wondering:

how would i use the cd to install from WITHIN ubuntu?

because for some reason it does not work on CD boot.

just a load of errors like packet could not be read etc. (that is just after the orange loader bar aswell)

thanks :)

---

### Post by Fire_Chief on 2008-06-19
If you're getting those kinds of errors when attempting to boot from the 8.04  CD, it sounds like you have a bad burn or a bad download. Try re-downloading the 8.04 ISO image and burn it again (possibly at a slower speed).

Also, to perform an in-place upgrade (not a clean install), use the Alternate Install CD image instead of the standard desktop version.

Cheers!

---

### Post by avtolle on 2008-06-19
Hmm, sounds like you have a corrupted iso file that you burned, a bad burn to the CD, or both. Not to be condescending here, but did you check the md5sum of the downloaded iso (in terminal, (assuming you d/l the iso to your desktop) prompt$>cd Desktop prompt$> md5sum NAMEOFISOFILE) against the md5sum given for the iso on the download page; burn as an image at a slow speed (I have found that 4x is appropriate) to a CD-R; then, on booting, check the integrity of the CD (menu item #4, I believe) before trying to run it?

---

### Post by 0perator on 2008-06-19
its a real cd, sent to me by shipit, it ran fine yesterday (from boot), but i didnt have time to install it so i came back today...

how big is the alternate cd thing?

---

### Post by avtolle on 2008-06-19
Hmm again; if the cd booted fine yesterday, upon receipt, and isn't booting today, what has happened to the cd in the meantime (did it get scratched, are there fingerprints on it)? Also, by any chance did you start to install yesterday and abort?

---

### Post by 0perator on 2008-06-19
the cd seems fine and clean, and no i did not abort.

i am downloading the alternate cd now anyway, hopefully that will work.

---

### Post by Fire_Chief on 2008-06-19
From the Ubuntu main site:

Upgrading using the alternate CD/DVD

Use this method if the system being upgraded is not connected to the Internet.

   1.

      Download and burn the alternate installation CD.
   2.

      Insert it into your CD-ROM drive.
   3.

      A dialog will be displayed offering you the opportunity to upgrade using that CD.
   4.

      Follow the on-screen instructions.

If the upgrade dialog is not displayed for any reason, you may also run the following command using Alt+F2:

```
gksu "sh /cdrom/cdromupgrade"
```

Or in Kubuntu run the following command using Alt+F2:

```
kdesu "sh /cdrom/cdromupgrade"
```

---

