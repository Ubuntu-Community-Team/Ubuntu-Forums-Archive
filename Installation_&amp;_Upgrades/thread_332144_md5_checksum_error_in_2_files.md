---
title: "md5 checksum error in 2 files"
date: 2007-01-05
forum: Installation &amp; Upgrades
---

### Post by dflives on 2007-01-05
i am in a desperate position downloading ubuntu-6.10-alternate-i386.iso, with consistent md5 hash fails on two particular files:
\install\netboot\pxelinux.cfg
\install\netboot\pxelinux.0

both files are currently 0kb

can anyone upload these 2 files, as im having the same problem over and over again even with a re-download or from a different source.

help always greatly appreciated. :D

---

### Post by Matt Reynolds on 2007-01-27
Hi

Are you checking under Windows? I got the same errors under Windows when using md5sum under cygwin and the tool from [http://www.md5summer.org](http://www.md5summer.org).  I looked at the two files under Linux and they are symbolic links and I believe Windows does not support symbolic links, therefore this is likely the reason for the error.  Can you run md5sum under a Linux box? If not and these are the only two errors you get I suspect your disk is OK.

Matt

---

### Post by JamieC on 2007-01-27
You can confirm the media is working by burning it irregardless of the md5 checksum failures, and using the media check option on the disk after booting it.

---

