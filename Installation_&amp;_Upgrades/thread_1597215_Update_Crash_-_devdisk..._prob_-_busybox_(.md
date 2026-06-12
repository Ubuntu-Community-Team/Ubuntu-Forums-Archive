---
title: "Update Crash - /dev/disk/... prob - busybox :("
date: 2010-10-15
forum: Installation &amp; Upgrades
---

### Post by puca mor on 2010-10-15
Hi,

Wondering if anyone has any advice on dealing with a boot error, where it first says:

> udevadm trigger is not permitted while udev is unconfiguredthen it tells me it's bored of waiting and:
>  Alert! /dev/disk/by-uuid/.....0000000... does not existThe zeros there represent what i presume is the uuid number?

This happened after my computer crashed during an update - the update was just installing, then the computer cut out dead - followed by that message on trying to boot up again.

I've been searching for answers and tried various solutions, no luck so far. I think most of the solutions were to restore GRUB; which doesn't seem to be the problem. 

Forgive my ignorance (i have a lot of it) - i checked the /dev folder, which on the original File System has only 89 files... the /dev folder on my recovery install has 135 (or thereabouts)... so it seems as if the update may have been changing those files when it crashed? (thats my best idea for what's going on)

Running 10.04LTS
Update attempt was last night (14th)

Thanks for any advice you can give me, also i know i have been scant with system details here - but i'm unsure how i go about getting the relevant details for the install which is now broken (?)

[Edit] Also - i have access to the file system of the original install... if that helps with getting info?

---

