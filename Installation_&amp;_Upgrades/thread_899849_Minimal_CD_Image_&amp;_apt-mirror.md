---
title: "Minimal CD Image &amp; apt-mirror?"
date: 2008-08-24
forum: Installation &amp; Upgrades
---

### Post by Xyem on 2008-08-24
Basically, I have used apt-mirror to create a mirror of several ubuntu repositories ( hardy *, hardy-updates *, hardy-security * [ where * means main, restricted, universe, and multiverse and in the case of hardy: main/debian-installer too ] ).

I have now rsync'ed the 'ubuntu' directory in the mirror to my USB drive so I can carry it around with me, primarily for use at work where I do not have an easily accessible network connection or ( and this has happened twice ) I am asked to install Ubuntu on a colleagues laptop ( none removed AFAIK so far :) ).

One situation I will, most certainly, find myself in is wanting to install from a Minimal CD Image and use my USB drive as the repository. The repository is required quite early on in the installer and I am not sure how to get the installer to look at a mounted partition. While at home, I can just point it to the apache server running on a networked computer but this won't be available in these instances.

Is there a way to, effectively, install from the Minimal CD Image without a network connection, using just the mirror on a partition? This would be very useful. All help is appreciated :) Thanks

---

### Post by Xyem on 2009-02-26
Anyone have any idea?

---

### Post by vikjon0 on 2009-08-19
There are installers that can scan a number of CD's for available packages as part of the installation process. I am not if it was debian that had this functionality.

You can add a cd to the sources.list for sure.

Maybe you could skip the mini cd and use the server CD instead and then edit the sources when you have command line..otherwise I guess you need to edit the image. Also, it will not mount the USB?

---

