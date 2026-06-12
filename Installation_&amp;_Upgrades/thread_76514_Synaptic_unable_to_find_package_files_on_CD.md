---
title: "Synaptic unable to find package files on CD"
date: 2005-10-15
forum: Installation &amp; Upgrades
---

### Post by kevin1 on 2005-10-15
I have downloaded ubuntu-5.10-install-i386.iso and burned it to a CD. The CD MD5 checksum is ok.
Following the advice from [https://wiki.ubuntu.com/BreezyUpgradeNotes](https://wiki.ubuntu.com/BreezyUpgradeNotes), I did:
     sudo apt-get install ubuntu-base ubuntu-desktop
... which informed me that both were already up-to-date.

I then opened Synaptic and clicked on "Edit/Add CD-ROM"

An error window then popped up:
     'E: Unable to locate any package files, perhaps this is not a Debian Disc'

Any ideas please?

Kevin

---

### Post by kevin1 on 2005-10-18
I eventually discovered a solution, and another problem:
With Synaptic closed I inserted the CD. A window popped up stating that it was recognised as a Ubuntu disc and asking if I wanted to start Synaptic. I answered Y and the disc was scanned for index files. I then updated from the disc. During this process I noticed lots of perl warnings rushing by in the Synaptic terminal window, but too fast to read. A short while after locales were being updated, Synaptic disappeared. I rebooted and just got a terminal screen, no Xwindows. At this point I gave up on the upgrade, booted from the CD and did a fresh install.

This works fine, except I have a problem with OpenOffice - which will be the subject of another post.

The great news is - sound works! I never got sound to work in Hoary.

Kevin

---

