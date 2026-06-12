---
title: "Clean install fails."
date: 2007-05-06
forum: Installation &amp; Upgrades
---

### Post by Harrkev on 2007-05-06
Hi.  I decided to completely  wipe my entire hard drive (well, both of them).

I go through custom partitioning, and then install, which fails about half-way through.  The installer just quits -- no error messages or anything.  When I re-boot, I so straight into Windows, so GRUB is not even being installed.  How can I fix an error if I do not know what the problem is? :cry:

I never had this problem with Dapper (never tried Edgy).

Athlon - socket  754
nVidia nForce Mobo
nVidia Graphics
1GB RAM
Pair of 80GB _SATA_ drives.

Primary hard drive:
  Windows XP - 45G
  Primary Linux ("/"), Ext 3, 25G
  Swap, 2G

Secondary hard drive
  NTFS Data - 55G
  EXT3 - 20G (maybe one day for Linux from Scratch)

---

### Post by raja on 2007-05-06
Are you using the live cd? If you have problems with it, you can try the alternate installer. Time and again it seems to rescue people when they have problems with installation from the live cd.

---

### Post by Harrkev on 2007-05-06
I will try that.  Thanks.

I still think that it is odd that I would not even get an error message...

Oh well.

---

### Post by Harrkev on 2007-05-07
Using the alternate installer worked.  Everything is shiny now. :)

A more interesting questions is: why did the regular install fail?

Using the live-run CD, I also found that Firefox would also just die sometimes.  Curious.

Well, I am just happy to have everything running, but somebody should look into these failures for "Grumpy Groundhog" or "Gassy Gnu" or whatever the next version is.

Thanks for the help.

---

### Post by raja on 2007-05-07
Glad that things are working.
It is just that the text-based installer has been around much longer and is likely to be more stable.
Its Gutsy Gibbon, by the way.

---

