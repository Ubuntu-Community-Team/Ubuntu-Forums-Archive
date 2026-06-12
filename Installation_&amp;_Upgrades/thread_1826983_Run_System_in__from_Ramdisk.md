---
title: "Run System in / from Ramdisk"
date: 2011-08-17
forum: Installation &amp; Upgrades
---

### Post by jb.transfer on 2011-08-17
Hi all,

I am trying to put a small system on a squashfs Image to run the OS entirely in RAM.

I have tried the BootToRam document and read a lot of articles and howtos.

Actually I want to be able to have the System running in RAM which keeps Track
of changes.

It seems that the LiveMedia Toram option is not the choice I need.  :confused:

Does anyone have a link to docs which I could use as a starting point?
Will I have to play with embedded linux?

cheerio jb

PS: Is it possible to put the whole system into an initrd?


Did some more tests:

3/9/2011
I have a Live System running either in ramdisk or from a loopmounted
squashfs image.
Am trying to mount 2 rw partitions for var and home. The casper scripts do
some strange things in var so mysqld is not working as expected.
Will do some research to figure out if this can be handled. Please let me
now if anybody has an idea. I will soon post the logs.

---

### Post by jb.transfer on 2012-03-05
Found the reason. I had to reconfigure apparmor.d

Also the following might help.

[http://ubuntuforums.org/showthread.php?t=1827669](http://ubuntuforums.org/showthread.php?t=1827669)

---

