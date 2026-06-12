---
title: "boot error when persistent from USB"
date: 2008-05-15
forum: Installation &amp; Upgrades
---

### Post by justin_guerin on 2008-05-15
Hi,

I have 8.04 installed on my USB stick.  When I boot just the live system, it works great.  When I boot the persistent option, I get dumped into ash, where I found this log entry:

mount: Mounting /dev/sdb2 on /cow failed: Invalid argument
Can not mount /dev/sdb2 on /cow

I tracked this down to the file /usr/share/initramfs-tools/scripts/casper, from the package casper, which is executing this line:

    mount ${cowdevice} -t ${cow_fstype} -o rw,noatime,mode=755 /cow || panic "Can not mount $cowdevice on /cow"

The reason this fails is because mode=755 is an illegal option for my fs type, ext2.  This option is only allowed on affs, devpts, iso9660 and tmpfs.  Obviously, casper was written to be used from a CD, so it makes sense that iso9660 is a supported file system.  However, I want to run a live, persistent system where casper-rw is ext2.

My question: is this a bug in the casper package, or should I replace casper with live-initramfs?  That is, maybe this is the reason for the fork?

FYI, if I manually mount the casper-rw partition (by leaving off the mode= option), then exit from ash, bootup proceeds normally, and all works as expected.

Thanks for any insight.

Justin

---

