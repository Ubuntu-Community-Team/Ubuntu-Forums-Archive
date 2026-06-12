---
title: "Sharing ext2/3 partitions with Vista"
date: 2007-05-06
forum: Installation &amp; Upgrades
---

### Post by msandersen on 2007-05-06
For those of you who are dual-booting with Windows Vista and wondering how to share your Linux ext2/3 partitions under Windows:

I just talked to Stephan Schreiber, the developer of the ***[Ext2IFS]("http://www.fs-driver.org/index.html")*** driver for windows, by email. A new Vista-compatible version will be released in a few days after he gets the last few bugs out.

Some features of the new version:
- Global Read-Only option,
- UTF-8 encoding,
- htree directories,
- supports Windows XP x64, Vista/Vista x64,
- supports PlugnPlay,
- file names starting with a '.' will be treated as hidden files.

In combination with the stable *NTFS-3G* driver for Linux for reading and writing NTFS, you will always be able to get at your files regardless of which OS you are using and which partiton they are saved on.

---

### Post by XTREEM|RAGE on 2007-05-09
this is what we need :D.
Cant w8 to get it on my system :)!

---

