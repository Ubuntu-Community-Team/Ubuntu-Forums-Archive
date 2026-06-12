---
title: "Btrfs support in Jaunty a maybe??"
date: 2009-01-10
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Slug71 on 2009-01-10
I guess if Jaunty ends up shipping with the 2.6.29 Kernel we may just have Btrfs support. :)

[http://www.phoronix.com/scan.php?page=news_item&px=Njk4Mw](http://www.phoronix.com/scan.php?page=news_item&px=Njk4Mw)

Not a very long life for Ext4 though. :(

---

### Post by ShirishAg75 on 2009-01-10
those crazy developers. Now there would be a big fork in the community, those who would like to play with ext4 and those who would jump to btrfs. 
Wasn't btrfs supposed to be something which was gonna take a year or something. Did recession have something to do with it?

/me smells a big rat.

---

### Post by Quikee on 2009-01-10
Ext4 was in kernel for quite some time also until it was deemed stable in 2.6.28 (it wasn't in Ubuntus kernel however). btrfs will just only entered the kernel in a "experimental" and "in development" state - it will still be quite some releases until it can be considered stable for everyday use. It doesn't even yet contain most of the major features planed.

BTW.: The btrfs has a minimum capacity of a partition 256 MB and maximum also can not be reached. Why? Because it can't yet calculate how much space the filesystem will need and can't handle yet the situation when the disk is full correctly and to prevent damage it has such artificial limitation in-place. This is just to remind everyone in what state btrfs currently is. 

Also btrfs is in Ubuntu for quite some time now (btrfs-source and btrfs-tools in repository) for those who wanted it. You can compile it as a kernel module (easily via module-assistant).

---

### Post by gnomeuser on 2009-01-10
> **ShirishAg75 said:**
> those crazy developers. Now there would be a big fork in the community, those who would like to play with ext4 and those who would jump to btrfs. 
Wasn't btrfs supposed to be something which was gonna take a year or something. Did recession have something to do with it?

/me smells a big rat.

Btrfs is not finished yet, but it's very close to a 1.0 state. It still needs a lot of proving itself to be labelled stable for production use. There are as far as I know still data format breakage to be done but there is no expectation of stability so it can go in now.

Btrfs has the advantage of being a completely fresh codebase, there was no ext3 cruft code to clean up, no existing quirks to consider. In that sense some things have been faster, others slower than expected.

Just to be clear, do not put data on btrfs you care about, the data format might change and then you are screwed unless you plan your migration. It is in the mainline kernel to focus development instead of having it in a separate tree, it's a sign that we are getting close but it is for people who know how to file a bug, write a test case and hopefully know how to read the btrfs code not for joe average just yet. If support is to arrive in jaunty I would advocate it being in the same form Fedora used for ext4 while it was in development. You pass a special parameter to the install media which enables it as a choice, preferably the parameter will be something like "i-understand-that-if-it-breaks-i-get-to-keep-both-pieces"

That being said I did not expect it to be merged without more reviews on lkml but now.. let the party begin.

---

### Post by LordVeovis on 2009-01-10
> **ShirishAg75 said:**
> those crazy developers. Now there would be a big fork in the community, those who would like to play with ext4 and those who would jump to btrfs. 
Wasn't btrfs supposed to be something which was gonna take a year or something. Did recession have something to do with it?

/me smells a big rat.

There are advantages to either ext4 and btrfs.  So I dont think that it will pose any potential problems.

---

