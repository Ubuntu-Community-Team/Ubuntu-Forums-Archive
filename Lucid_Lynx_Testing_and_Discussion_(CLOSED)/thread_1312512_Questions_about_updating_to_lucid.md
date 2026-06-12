---
title: "Questions about updating to lucid"
date: 2009-11-03
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by mrsurb on 2009-11-03
I have a couple of questions relating to how to get to bleeding edge lucid as fast as possible:

1) The kernel 2.6.32-2 is in the repositories and I could apt-get install it manually, but apt-get dist-upgrade does not give the option. "apt-get cache policy linux-image-generic" gives 2.6.31-14 still. Should I just update manually?

2) If I replace all of the "karmic"s to "lucid"s in /etc/apt/sources.list will I still get the updates that will appear in karmic-updates, karmic-backports and karmic-proposed?

Enjoying the bleeding edge!

---

### Post by jfernyhough on 2009-11-03
> **mrsurb said:**
> I have a couple of questions relating to how to get to bleeding edge lucid as fast as possible:

1) The kernel 2.6.32-2 is in the repositories and I could apt-get install it manually, but apt-get dist-upgrade does not give the option. "apt-get cache policy linux-image-generic" gives 2.6.31-14 still. Should I just update manually?Yes. linux-generic only gives the upgrade once all the component packages are available (e.g. restricted-modules). This generally takes a while longer to appear than linux-image - if you don't need restricted-modules then there's no need to wait. My drivers and modules (nvidia, virtualbox) even seemed to compile correctly with .32. Nice.

> 2) If I replace all of the "karmic"s to "lucid"s in /etc/apt/sources.list will I still get the updates that will appear in karmic-updates, karmic-backports and karmic-proposed?
No. The karmic updates will only appear in lucid if they are uploaded to the lucid repos. However, you should find that in a couple of weeks the lucid versions are a higher version than the karmic updates (we get the bleeding-edge stuff! Yay!).
> Enjoying the bleeding edge!Yup. Just make sure you're ready for it to fall over and die. I have two backup installs on USB drives (one backup Karmic and one Jaunty from an old laptop). This means I can chroot and update/fix and I have a backup of work etc. so I can keep working anywhere (on any machine) in the worst case.

---

### Post by mrsurb on 2009-11-03
Thanks for the reply. I have a copy of a clean karmic install, and all of my work is daily backed up to my file server

---

