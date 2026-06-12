---
title: "Maverick has its own ideas about my drive device names."
date: 2010-12-14
forum: Installation &amp; Upgrades
---

### Post by negativ on 2010-12-14
I'm trying to install Xubuntu 10.10 onto a machine with 3 hard drives.  

My drives are (rather, *should be*) like this:
/dev/sdaX: Windows and Windows apps/games
/dev/sdbX: Data
/dev/sdcX: Blank drive for Linux.

This corresponds to BIOS order, as well as to the order the drives are physically connected to the motherboard (SATA0, SATA1, SATA2)

Every other distro I've tried, including Ubuntu proper and Kubuntu, Arch, and Fedora, all display the expected behavior.  The Xubuntu installer, however, insists on swapping /dev/sda and /dev/sdb.

Is there a quick-ish fix for this?

---

### Post by negativ on 2010-12-15
Apparently, this may have had something to do with booting the live image from USB, but I don't know why.  I ran it from CD and all was well.

---

