---
title: "Problems in running apt-get update"
date: 2012-02-26
forum: Installation &amp; Upgrades
---

### Post by beforewisdom on 2012-02-26
Hi;

I'm on Ubuntu 10.10

For the last several months I have been using apt-get update instead of the update manager. The latter simply does nothing when I hit the "authenticate" button.

Today when using apt-get update I got something odd:

> 
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/non-free i386 Packages
Media change: please insert the disc labeled                                   
 'Xubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101008.1)'
in the drive '/cdrom/' and press enter

I installed Xubuntu a few months back and removed it.   I never used a cd.

I've relied on the update manager for a long time so I have no idea of how to fix things with package lists.

Could someone tell me how to fix this problem and possibly get update manager working again?

Thanks

---

### Post by slugmax on 2012-02-26
You can manage your sources graphically with 'Software Sources' under the settings menu. You can also manually edit the /etc/apt/sources/list:

```

sudo nano /etc/apt/sources.list

```

Substitute your editor of choice for 'nano'. Look for the cdrom line and delete or comment it out.

---

### Post by beforewisdom on 2012-02-26
Thank you.

I commented that line out and that solved the problem.

---

