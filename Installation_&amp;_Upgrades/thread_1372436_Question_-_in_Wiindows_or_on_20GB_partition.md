---
title: "Question - in Wiindows or on 20GB partition?"
date: 2010-01-04
forum: Installation &amp; Upgrades
---

### Post by TJGeezer on 2010-01-04
Hi,
I installed 9.10 successfully using Wubi on a Vista64 system. This new version is SO much clearner and easier to use than earlier Linux distros I had tried, I decided to stay with it. When I got a supported graphics card I wiped the installation, made a 20G free space on another drive, and installed there, thinking it would be faster.

It wasn't - SATA150 instead of SATA300 had a speed penalty, duh. So I gave the space back to NTFS and now I'm stalled. So... -

Is the speed penalty of installing with Wubi onto an existing NTFS Vista partition appreciable? I can carve 20G out of the faster drive for a separate Ubuntu partition set  if that would be better.  Problem last time when I installed onto a separate Ubuntu partition was, it didn't give me a dual boot option (which I need). The only way to select was to change the BIOS HDD order between boots, which is a hassle. And which won't be possible if I install onto a partition on the same HDD as Windows.

I liked Ubuntu when installed on the Windows partition, but since it thinks it has an Ext partition I suspect it creates a file-based "virtual" partition on top of the NTFS, kind of the way TrueCrypt does for encrypted volumes. Doing that with an OS partition makes me nervous - it just FEELS like asking for problems. But on its own partition, Ubuntu doesn't seem to recognize the need for a dual boot.

Advice? = and many thanks in advance!

:confused:

---

