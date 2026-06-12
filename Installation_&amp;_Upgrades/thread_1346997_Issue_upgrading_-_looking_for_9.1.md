---
title: "Issue upgrading - looking for 9.1??"
date: 2009-12-05
forum: Installation &amp; Upgrades
---

### Post by PerfectReign on 2009-12-05
I have an update manager screen appearing. (I'm on 9.04, GNOME.)

When I go to install updates, which include a new kernel (2.6.28-17), I get the message that it wants me to install the 9.1 CD in my optical drive. It reads: "Please insert the disk labeled:Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)
in drive /cdrom/"

I then get a message that, "W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-source_2.6.28.17.22_all.deb"


What's up with that?

---

### Post by dhavalbbhatt on 2009-12-05
> **PerfectReign said:**
> I have an update manager screen appearing. (I'm on 9.04, GNOME.)

When I go to install updates, which include a new kernel (2.6.28-17), I get the message that it wants me to install the 9.1 CD in my optical drive. It reads: "Please insert the disk labeled:Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)
in drive /cdrom/"

I then get a message that, "W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-source_2.6.28.17.22_all.deb"


What's up with that?

Not sure if you tried upgrading to 9.10 before, maybe a partial upgrade from the past needs to be completed?

I would also check the software sources and under Ubuntu Software, uncheck any options under "Installable from CD ROM/DVD" - provided they are checked.

---

### Post by PerfectReign on 2009-12-05
No, never tried to upgrade, but I did - at one time - have 9.1 in the DVD drive.  Maybe somehow it got added to my sources.

I removed it.  

That worked. :D

---

