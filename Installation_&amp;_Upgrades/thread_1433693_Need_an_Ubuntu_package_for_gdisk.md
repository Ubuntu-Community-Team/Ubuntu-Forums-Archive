---
title: "Need an Ubuntu package for gdisk"
date: 2010-03-19
forum: Installation &amp; Upgrades
---

### Post by Skaperen on 2010-03-19
With GPT partitioning more and more needed (MSDOS partitions not supporting drives larger than 2TB), and fdisk and sfdisk not supporting GPT, and parted still being cranky, I'm looking for another partitioning tool.  There is a project called "gdisk".  But I can't find an Ubuntu package for it.  I guess I'll have to build that one from source.

Is there a place to suggest adding the package?  I guess the alternative is to learn how to build my own Ubuntu packages.

Or if I can find enough docs on the partition table structures, maybe I can write my own that will be even easier to use from the command line (letting someone else make the GUI eyecandy around it).

---

### Post by srs5694 on 2010-03-19
A package is already in the 10.04 version of Ubuntu; [see here.](http://packages.ubuntu.com/lucid/admin/gdisk) It's already a bit elderly, though; it's version 0.5.1, vs. the current 0.6.5. You can download Debian packages of the latest version from the GPT fdisk [Sourceforge downloads page.](http://sourceforge.net/projects/gptfdisk/files/)

FWIW, I'm the author of GPT fdisk. Before each release, I do a test install of the i386 and amd64 Debian packages on Ubuntu systems (9.04 and 9.10, IIRC), although my PowerPC test system runs Debian. If you have problems, you could try installing alien (and its rpm dependencies), rebuild the source RPM, and use alien to convert it to a Debian package. That's actually how I create my Debian packages. Ironically, I build my i386 RPMs on Ubuntu; they seem more portable than the RPMs built under Fedora or SUSE. (I've been using Gentoo to build my recent x86-64 RPMs.)

As to documentation on GPT, check [the Wikipedia page](http://en.wikipedia.org/wiki/GUID_Partition_Table) on the topic. The formal and official specification is available [here,](http://www.uefi.org/specs/) as part of the UEFI specification. I used the Wikipedia page as my primary reference when writing GPT fdisk.

---

### Post by Skaperen on 2010-03-22
Maybe they can let you be an Ubuntu package maintainer and then you can keep the Ubuntu package up to date (even if it's just a copy of the Debian package).

---

