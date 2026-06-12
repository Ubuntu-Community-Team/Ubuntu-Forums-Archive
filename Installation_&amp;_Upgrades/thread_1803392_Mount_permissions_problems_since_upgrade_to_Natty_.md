---
title: "Mount permissions problems since upgrade to Natty 11.04"
date: 2011-07-13
forum: Installation &amp; Upgrades
---

### Post by robbennett75 on 2011-07-13
Hi,
My system isn't behaving properly.  I attach my USB camera and get a popup "Unable to mount New Volume Not Authorized".
If I use system->disk utility the drive is shown, but the mount volume button gives:

Error mounting volume an error occurred while performing an operation on "New Volume" (Partition 1 of FUJIFILM USB-DRIVEUNIT): Permission denied.

I get the same message when trying to mount DVD too.

If I sudo palimpsest I can mount the volume and access until I close disk ulity.

I did discover that I wasn't a member of the fuse group, but I've now added myself and it's still not resolved.

I'm on 11.04, having upgraded from a couple of previous versions of ubuntu successfully.

```
rob@claret:~$ uname -a
Linux claret 2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:05:41 UTC 2011 i686 i686 i386 GNU/Linux

```I hope someone can guide me to resolve this.

Rob

---

### Post by Morbius1 on 2011-07-13
I'm not good with hardware issues but after adding yourself to a group you need to logout and login again for the group membership to change. Did you do that?

---

### Post by robbennett75 on 2011-07-13
Yes, I gave the machine a reboot.

It doesn't feel like a hardware problem.   If I sudo I can make it work, so this must be a permissions thing, right?

Rob

---

### Post by robbennett75 on 2011-07-17
I have the same problem with optical disks that I do with my usb camera.

If I sudo palimpsest, it will let me mount the volume, although the media gets mounted in such a way that my user can't access it.
If I run palimpsest as my own user, when I click mount volume, I get:

Error mounting volume
An error occurred while performing an operation on "LTE0NNW1" (Whole-disk volume on TSSSTcorp TSSTcorp CDDVDW SW-S223C): Permission denied
Details
Not Authorised.

Where is the right to mount volumes defined?

Rob

---

