---
title: "&quot;No room&quot; for all updates for Ubuntu Live Persistence"
date: 2010-11-30
forum: Installation &amp; Upgrades
---

### Post by Bitech on 2010-11-30
So I make a Bootable Ubuntu Live CD with 4GB Persistence on my USB. Everytime I try to download all the 350~MB updates my persistences suddenly runs out. How and why are the updates taking so much more space than their actual download sizes?

And is downloading and installing SOME of the updates at a time the only way to get them all installed? Because I always run into installation errors with the updates.

Thanks

---

### Post by efflandt on 2010-11-30
You can add programs, but should not really try doing updates to an iso on usb because anything that loads before persistent data is mounted is fixed in a squashfs file system and not easily changed (without rolling your own iso).  Kernel or grub updates or proprietary video drivers in particular will fail, because initramfs will fail.

If you want to do updates to a system on USB flash, you should get a large enough one (8 GB or larger recommended) to do a regular install (probably using ext2 file system).  Just make sure that you put grub on the USB stick, not your main drive mbr.  You should manually partition it (before hand or during install) and use the **manual partition screen during install**, because the selection **where to put grub is at the bottom of that screen**.

---

### Post by Bitech on 2010-12-01
I forgot to mention I use LiLi to make my live cds. and my usb is 8gb. what livecd making software are you basing your steps off?

---

