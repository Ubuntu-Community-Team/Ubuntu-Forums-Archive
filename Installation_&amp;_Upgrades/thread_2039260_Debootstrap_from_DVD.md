---
title: "Debootstrap from DVD?"
date: 2012-08-08
forum: Installation &amp; Upgrades
---

### Post by ZOMFG on 2012-08-08
Hi guys,

I am currently trying to do my first debootstrap and it seems i'm failing miserably.

My aim is to bootstrap a ubuntu/xubuntu system into the current one and then run virtualbox headless from it (disks will be stored outside of the bootstrapped OS).

At this point im wondering if I will be capable of setting up a distro from scratch seeing as how debootstrapping the generic ubuntu version will give me a barebones distro and I will have to configure most of it via terminal.

I was wondering if it is possible to tell the debootstrap command to use the xubuntu/ubuntu DVD's I have, as sources for the new bootstrap system.

Would that be possible and if so, how would one go about doing this?

I have tried the following command but get errors:

**sudo debootstrap --arch i386 precise /mnt/ubuntu file:/cdrom/ubuntu/dists/precise/main/binary-i386**

It returns - 
[COLOR=Red][I][B]I: Retrieving Release
E: Failed getting release file file:/cdrom/ubuntu/dists/precise/main/binary-i386/dists/precise/Release[/B][/I][/COLOR]

Seeing as how im a complete newb in this, im sure Im not doing it correctly. Would anyone be able to help out?

Many thanks.

---

