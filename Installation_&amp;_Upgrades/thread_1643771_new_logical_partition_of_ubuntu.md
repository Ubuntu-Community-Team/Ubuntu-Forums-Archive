---
title: "new logical partition of ubuntu"
date: 2010-12-12
forum: Installation &amp; Upgrades
---

### Post by pjmlmas on 2010-12-12
Windows is on primary partition

I have an instance of Ubuntu 10.04 on a logical partition in an extended partition.

I works fine.

I create a new logical partition in extended partition.

When I go to install a second instance of Ubuntu off of the live CD, what is supposed to happen?

How does grub2 get updated?i.e.
Does the GRUB2 in the MBR get updated?
Does the "second stage" get updated? Where is the second stage?
What happens with the second instance?
How does it get added to the menu? And where is this information stored?

I see that there are updates for grub2 in update manager.
If I update grub2 in first instance, what does this mean when I install 10.04 which does not have this update?
This question comes from the following quote:
> The menu that you see on the screen when you boot up comes from the /boot/grub/grub.cfg file.
Where is this /boot/grub/grub.cfg in regards to multiple Ubuntu instances? Every instance gets a copy? If so, what happens with different patches of GRUB2.
Any information is appreciated.

---

### Post by coffeecat on 2010-12-12
If you already have Ubuntu installed on your machine and you install a second instance of Ubuntu on another partition, and if you allow the installer of the second installation to install grub, then it will pick up the presence of the first Ubuntu and set up a grub menu to allow booting of all the OSs on your machine. It will also install its version of grub stage 1 to the mbr pointing to grub in the root partition of the new installation.

I know this to be true. I have Jaunty, Karmic, Lucid, Maverick, two instances of Natty Alpha (long story), Fedora 14, Gentoo, **and** Windows 7 on this machine. My grub menus get to be a bit lengthy. :)

To pick up your other points, strictly speaking grub 2 doesn't have a stage 2 as such - you had a stage 2 file in legacy grub - but it has a large number of modules that cover the functions of stage 2. You can find them in /boot/grub. Every instance of an Ubuntu installation will have its own /boot/grub/grub.cfg, but only one will be relevant, because grub stage 1 in the mbr will point to one Ubuntu root partition only. In fact it's not quite correct to say that grub stage 1 points to a root partition. There is some more grub code in the embedding area - that's an otherwise unused section of the hard drive between the partition table and the first sector of the first partition. In legacy grub this was called stage 1.5. I don't know what it's called in grub2. 

Any more questions? :p

---

