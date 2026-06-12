---
title: "Best way to install another  Kubuntu ..."
date: 2007-02-04
forum: Installation &amp; Upgrades
---

### Post by reiki on 2007-02-04
OK I think I'm just having a senior moment but I want to be sure I don't mess this up. I could probably fix whatever I break but trying to keep it simple.

I have:
3 separate hard drives
IDE (hda)
SATA (sda)
SATA(sdb)

My machine currently boots sda as first boot.

sda has Dapper on it.
I usually use GRUB to boot to Edgy on sdb

The IDE drive has 80gig WinXP on it with another 70 plus unformatted. I was thinking about tossing a Kubuntu install into the 70gigs on that IDE drive.

If I'm IN Edgy on sdb when I stick the Kubuntu CD in... will it want to install GRUB on sdb?  Or will it know that I've booted from sda and MODIFY the grub menu.lst on that partition?

What I DON'T want.... I don't want to destroy my grub menu.lst on sda. Modifying it is fine, but I don't want it replaced.

What do you think? Go ahead and install from here on sdb? Or boot to sda (Dapper) and install Kubuntu on hda from there?

---

### Post by bulldog on 2007-02-04
Just choose the right hdd when you come to the partitioner and everything should be fine.
You can easily modify GRUB if necessary but reinstall GRUB is just as easy with the live cd.

---

