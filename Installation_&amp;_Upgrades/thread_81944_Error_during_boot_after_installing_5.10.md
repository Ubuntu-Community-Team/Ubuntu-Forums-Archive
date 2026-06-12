---
title: "Error during boot after installing 5.10"
date: 2005-10-25
forum: Installation &amp; Upgrades
---

### Post by cwc on 2005-10-25
Howdy,

I've been using Ubuntu for awhile now, on my laptop and especially at work. After 5.10 was released I finally got around to installing it on my PC.

The first phase of the installation is error-free, as usual. After the system reboots and tries to load Ubuntu, it gets to the point where it's 'Uncompressing linux...' before the kernel panics with the message:

ALERT! /dev/hdf5 does not exist. Dropping to a shell!

Incidentally, it does not drop to a shell. It just freezes and ignores all keyboard input.

When I boot the install CD and switch to another virtual terminal, I can mount all the partitions I created, and all the necessary content appears to be there.
Also, I see all the device files in /dev that I expect to be there, though this probably doesn't matter since it didn't actually boot the kernel off the hard drive and map devices to those files.
If I enter the GRUB command line, instead of booting into Linux, and try a 'find /dev/hdf' or similar command, with the root set to (hd0,4), nothing is found. However, 'find /dev/fd0' returns positive, as expected.

I don't understand for sure why the hard drive -- the only one in this system -- is detected as /dev/hdf in the first place. I believe it may have something to do with the IDE controllers on my motherboard (Soyo KT880 Dragon 2) and how they are recognized by the BIOS.

I noticed a few other posts similar to this one in that the same error message is produced, however none seemed quite close enough to my problem, so I bugged the issue on bugzilla (it's #18379) and posted here.

Can anyone shed some light on this for me?

UPDATE: I found a Breezy preview disc I made back in September and reinstalled from it. Everything worked fine. After updating completely to the newest release and rebooting, I experienced the same bug again. If I choose to boot into the older kernel (2.6.12-8-386) from the preview release, it works fine.

I'm not at all sure, but I really think that the initialization/bootup process changed drastically between the two releases, and the kernel is no longer loading a module/driver needed to access my hard drive. The very first message I see when booting into the old kernel is something to the effect of "Setting up RAID controllers", and my lone HD is plugged into a RAID controller. This message is curiously absent when trying to boot the newest kernel, the first message before the panic being "Loading modules", which appears a good bit later when booting the working kernel.

I don't know what else to do. I suppose I'll just have to live with the old kernel until someone fixes this.

---

