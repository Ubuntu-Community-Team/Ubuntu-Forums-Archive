---
title: "Edgy &amp; FC6 Dual Parititon System is Using Grub On 2nd Partition Not the 1st"
date: 2007-02-12
forum: Installation &amp; Upgrades
---

### Post by tedrogers on 2007-02-12
Hi all,

This is not so much a problem, but more of a niggle and I'm trying to learn what goes on where.

Basically, I had a 20GB HD which had only Edgy on it like this:

/hdb1 /
/hdb2 [Extended partition]
/hdb5 /Swap

I split /hda1 into two partitions using gparted and created /hdb3, onto which I installed FC6. When going through the install process I set /hdb3 to be / and asked the installer to install Grub. It detected the Edgy installation fine, but didn't work when I tried to boot into it.

I solved this problem by editing the anaconda generated (FC6 installer) menu.lst file on /hdb3 [in /boot/grub] and added the relevant Edgy options from my working /boot/grub/menu.lst on the /hdb1 edgy partition.

Now what's bugging me is that the grub is working off /hdb3 (the drive with FC6 on it). This had all these unwanted FC6 boot-loader gfx that I didn't want as this is my Ubuntu ;) machine, so I disabled these to give me a plain OS selection menu...but I would much rather invoke the menu.lst from /hdb1 rather than /hdb3.

My current setup looks like this:

/hdb1 boot
/hdb3 /
/hdb2 extended
/hdb5 /swap

How do I do this...to get it to use grub off /hdb1 and not /hdb3? I don't understand especially as gparted reports that /hdb1 is the boot partition.

Maybe it's really simple...but I'm looking for config files that direct the relevant grub loader on whatever partition and I can't find anything.

Can anyone help?

Thanks in advance.

---

