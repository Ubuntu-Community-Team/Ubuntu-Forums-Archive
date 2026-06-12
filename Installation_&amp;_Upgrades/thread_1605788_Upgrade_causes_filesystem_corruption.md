---
title: "Upgrade causes filesystem corruption"
date: 2010-10-25
forum: Installation &amp; Upgrades
---

### Post by Perkins on 2010-10-25
I had 10.04 installed to an 8gb flash drive on an encrypted partition.  I installed it with EXT3 because EXT4 was reported to have serious file-system corruption issues when on USB flash.  (I can verify that those issues were present in 10.04 since I installed it on EXT4 once just to see, and had major problems with directories dropping out of existence.)

So, had it working for a couple of months, decided to upgrade it first before my hard-drive install just to see what issues were likely to crop-up.  (I have, occasionally, had an upgrade go 'blewy.)

First thing that happened was, when I tried to open firefox while it was downloading all the necessary stuff, it wouldn't work.  No errors, no nothing, just died.  No defunct processes floating around or anything.  That was odd.  

Then the upgrade threw a lot of errors about certain packages not being able to install.  Mostly KDE library packages.  They wanted to touch the /usr/share/doc/kde/HTML directory, but couldn't.  That was *really* odd...

So, when it was done trying to upgrade, I rebooted into my HD install, hooked up the encrypted partition, and fsck'ed it.  There were a *lot* of errors about inode sizes being wrong, invalid magic numbers, and the like, but the one that caught my eye was the one about the extent flag being set on a filesystem that does not support extents...

So, it seems to be all fixed now, I just finished reconfiguring all the damaged packages, everything seems to be working fine.  My .mozilla directory is gone, along with a few mailboxes and such, but nothing important since this is my "play with it and see what breaks" install anyway.  I'm just curious if the upgrade tried to change my filesystem to EXT4, or if anybody has any idea what the heck just happened...

---

