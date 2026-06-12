---
title: "Trouble with partitions/installation"
date: 2006-12-19
forum: Installation &amp; Upgrades
---

### Post by Nokkusu on 2006-12-19
First of all, I'm pretty much a beginner, so I just might have made stupid mistakes...

I've got trouble installing Ubuntu 5.04 (the CD is old, but I can always upgrade to the newest version after the install, right?).

I've currently got Windows XP installed on my harddrive and I'm using Power Partition Manager 2006 for partitioning.

I've made a Logical ext3 partition for Ubuntu, but whenever I try to install it it tells me that there is no partition found which it can use.

What exactly deo I need to do to make it work?
How many partitions do I need? (people in [this thread]("http://ubuntuforums.org/showthread.php?t=321489") are talking about 2).
And which format do they have to have?

---

### Post by Juan Largo on 2006-12-19
Nokkusu -

I would advise you to obtain the installation CD for the latest version of Ubuntu, rather than upgrading after installing an earlier version.

You need three partitions to install Ubuntu:  

1) ext3 for / (root)
2) ext3 for /home
3) Linux swap

Although I prefer to make my own partitions ahead of time, an alternate method is to create some unallocated space on your hard disk and let the Ubuntu installer do the partitioning for you.  

At this point in time, you could do one of the following:

1) Delete the ext3 partition you created and shrink the other partitions to leave about 15 GB of unallocated space,  Then direct Ubuntu to install itself in that space.

OR

2) Create another ext3 partion plus a Linux swap partition (if your partitioning tool does this).  During the Ubuntu installation, you will have to define "mount points" for these partitions.  If you're installing Ubuntu on the first hard disk with another OS partition already on it, these partitions will probably be labeled hda5, hda6, and hda7.  You could then "mount" hda5 to /(root), hda6 to /home, and hda7 to swap.  You will need to define "mount points" for your other non-Linux partitions as well.  This will enable you to access directories and files on these partitions.

---

### Post by Sef on 2006-12-19
You can make 2 or 3 partitions.   /Home is an option.  If you back up regularly you really don't need it; however, if you don't, then it can come in handy if you update your system with a clean install, or your system is borked for some reason.

Read the[ Illustraed Dual Boot]("http://www.users.bigpond.net.au/hermanzone/") for installing with the alternate cd.

Read [Psychocat's Installing]("http://www.psychocats.net/ubuntu/installing") for installing with the Live CD.

To partition, try [GParted]("http://gparted.sourceforge.net/livecd.php").  It's open source and no cost.

---

