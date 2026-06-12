---
title: "Can't update Ubuntu Professional from update tab"
date: 2024-10-16
forum: Installation &amp; Upgrades
---

### Post by frank2491 on 2024-10-16
When I tried updating from 22 to 24, I kept Error notices that there was some sort of a bad link to several of the software sources. I tried to resolve one involving Linux babe, but there was no reference to that in the sources.list. I tried to do a manual update by changing the sources.list names from the old distro to the new one. I did an apt-get dist-upgrade after apt-get update. Trying these before I made the changes only got new software under the old distribution. My computer downloaded about 3000 different programs, but somehow lost track of things and I was left at the command line with no workable way to restart or to connect to the Internet to finish the job. So I downloaded the ISO and installed 24.0 4.1 LTS.

---

### Post by grahammechanical on 2024-10-17
Not you are not the only person to misunderstand to function of apt-get dist-upgrade. It does not upgrade a Linux distribution to the next version. The man page says this:

> **dist-upgrade**
           **dist-upgrade** in addition to performing the function of upgrade, also intelligently handles changing dependencies with new versions of packages; apt-get has a "smart" conflict
           resolution system, and it will attempt to upgrade the most important packages at the expense of less important ones if necessary. The dist-upgrade command may therefore
           remove some packages. The /etc/apt/sources.list file contains a list of locations from which to retrieve desired package files. See also apt_preferences(5) for a mechanism
           for overriding the general settings for individual packages.

So, by running that command a lot of software packages were removed and replaced and it broke the OS. Re-installing is often the easiest way of putting things right.

Regards

---

