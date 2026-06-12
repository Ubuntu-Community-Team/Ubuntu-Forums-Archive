---
title: "transferring within a hard drive"
date: 2010-07-29
forum: Installation &amp; Upgrades
---

### Post by EuriskoXP on 2010-07-29
i have a Dell Latitude D820 with an upgraded western digital 500gb drive.
Originally i put 2 partitions on it;
120gb (NTFS)- win XP install
100gb (NTFS)- storage part

and added ubuntu 8.10 for a class project (custom install) later;

120gb (NTFS)- win XP install
100gb (NTFS)- storage part
50gb (ext3)- Ubuntu 8.10-2.6.26-custom

Recently i was unhappy with XP installed 10.04 with (ugh) 8gb through wubi (i know, "why the hell did i do that"). It took a lot of time to get it working right, especially with the damned wifi, but now im fast running out of space. I've worked out on paper what i want, and used gparted to arrange the following;

primary: 120gb (NTFS)- win XP install
primary: 100gb (NTFS)- storage part
extended:192gb-
logical:   4gb (swap)
logical:   8gb (ext4)- BackTrack4   *pending install!*
logical: 180gb (ext4)- Ubuntu 10.04 *pending install!*
primary:  50gb (ext3)- Ubuntu 8.10

now my question is:
how do i go about dropping my 10.04 installation AS IS onto the logical partition i created for it? I would like to avoid moving too many files around by hand if possible.
note: a friend suggested i make a liveinstall from the wubi install then use that to install onto the drive, but it didnt work. perhaps with remastersys?

tl;dr how to transfer a wubi install to fresh drive?

---

### Post by EuriskoXP on 2010-07-29
addendum:
inb4 "youre crazy/stupid/etc" "dont bother" and so forth. I use linux because I love the power of being able to do this stuff- make it run just how i like.

---

### Post by P4man on 2010-07-29
This only works up to 8.04:
[http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)

For anything newer I think you are out of luck.

---

### Post by EuriskoXP on 2010-07-29
aw thats a bummer...

i found this: 
[http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys)
any thoughts? it looks promising.

also:
If I just "gksudo nautilus" and dropped the files onto the new partition, would that work? (assuming I reconfigd GRUB appropriately)

---

### Post by EuriskoXP on 2010-07-29
shameless selfbump

anyone?

---

### Post by bcbc on 2010-07-29
Migrate wubi to partition howto: [http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

