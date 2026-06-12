---
title: "[SOLVED] installing windows"
date: 2007-11-24
forum: Installation &amp; Upgrades
---

### Post by jmagick07 on 2007-11-24
When I installed Ubuntu about 7 or 8 months ago, I completely uninstalled Windows.  But now I want to re-install it so I can use some programs that WINE doesn't run correctly.  I don't want to lose any of the files I currently have on the hard drive.  Is there a way to partition the hard , and install Windows on the new partition, without losing any of the files I have on Ubuntu?

Incase this is needed info: I don't have a Live CD of the current version of Ubuntu, I upgraded from the 'net.  I do however have a Live CD of the previous version.

---

### Post by ijason on 2007-11-24
yes, you almost certainly can do what you're wanting to. you'll boot off the live install cd and then in the >system>admin menu you use the partition editor (may be called gparted or partition manager, depending on your version).

then you select your primary drive from the pull-down menu on the right, and then click the big ext2 (or ext3) partition that is your main ubuntu install. you **should** be able to right-click and choose the 'resize/move' option. you can then reduce the size of your primary partition by 10 gigs or so. that will free up an equal amount of unused space.

you then make a new ntfs partition to take up all that freed up space, and use it to install windows :)

it takes a LONG time to resize partitions, so be patient. and you'll probably want at least 10 gigs for windows and its programs.

---

### Post by jmagick07 on 2007-11-24
> **ijason said:**
> you'll boot off the live install cd

So then I guess I should order the most recent Live CD then before doing this?

Thanks for the instructions :)

---

### Post by markusf21 on 2007-11-24
The live cd you have will work

---

### Post by jmagick07 on 2007-11-24
> **markusf21 said:**
> The live cd you have will work
Awesome thanks :)

---

