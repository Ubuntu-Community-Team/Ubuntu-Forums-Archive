---
title: "Partitioning for encrypted FS &amp; dual boot"
date: 2007-11-02
forum: Installation &amp; Upgrades
---

### Post by Dave / Mosaic on 2007-11-02
I'm going to be creating a new Ubuntu system over the next few days, and I'd like to know in advance if the following partition-resize operations will work.  (I've searched through the documentation and forum posts and concluded that this will work, but I'd like some confirmation if possible, in advance of actually diving into it.)

What I want to do, is:

1) Create an Ubuntu installation with fully-encrypted root, home, and swap, with only a trivial /boot partition unencrypted, using LVM, dm-crypt, etc., all within a single ReiserFS partition, as has been discussed numerous times already in these forums;

2) In creating the above Linux installation, I want to leave 50 GB or so space at the end, in which to put Windows XP on its own partition, thus making a dual-boot machine;

3) However, in a couple of months, once the Windows installation is no longer wanted, I want to wipe out XP's partition with dban, turn the partition into free space, and then expand the Linux system's ReiserFS partition and encrypted logical volume to fully use the free space, as though I had given the whole free space to the Reiser FS to begin with.

As far as I can tell, I think this will work; the relevant tools seem to support the expansion of the Reiser partition and logical volumes.  But, I'd like to be more sure in advance, never having done this before, so as to not have to waste a lot of time fixing things later on.

Any thoughts??

--thanks

---

### Post by michaelzap on 2008-02-13
* Bump! *

I'm trying to do something similar, and I can't figure out how (or even if it's possible in Ubuntu)...

I have a laptop with an existing Vista installation (which for now I'd like to keep, although I expect that it won't last long). I'd like to add Ubuntu to this drive with the root, home, and swap partitions encrypted. I'm not particularly concerned with whether the Ubuntu partitions are ReiserFS or ext3, but I definitely want them properly encrypted.

I can't figure out how to set up the partitions using the alternate install CD so that I can use an encrypted LVM and not wipe out my existing Vista installation.

---

