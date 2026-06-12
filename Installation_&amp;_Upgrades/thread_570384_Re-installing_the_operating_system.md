---
title: "Re-installing the operating system"
date: 2007-10-08
forum: Installation &amp; Upgrades
---

### Post by DrewB on 2007-10-08
Hello fellow Ubuntu users!
It seems that an Ubuntu installation degrades over time. I have been running Ubuntu (first Edgy then Feisty Fawn) for about a year. Over this time things have started to degrade - I get a ****** up(technicall term) login screen sometimes and the sound has stopped working.

To try and remedy this and clean things up I wish to re-install the OS when the new version of Ubuntu (Gutsy Gibbon) comes out in 10 days time.

The OS is on its own root(/) partition and I have separate partitions for /home /usr and /opt.

My question is: do I do a new install of Gutsy to root, after first backing up /etc/fstab, overwriting the old installation, and then replace the /etc/fstab with the backed-up version?
Then I can remove the newly created /home /usr and /opt from the new installation?
Of course I would back up my /home /opt and /usr partitions before doing anything.

Have I got this right?
Any advice anyone can give me on re-installing the OS with separate partitions for / and /home would be very gratefully received.
Kind regards
Andy Birchall

---

### Post by dabl on 2007-10-08
> **DrewB said:**
> 

It seems that an Ubuntu installation degrades over time. 

You mean like sandstone weathering over the centuries, or some natural force of degradation?  :)

Probably there was an actual (intended or otherwise) change in the configuration of your system.

> 

The OS is on its own root(/) partition and I have separate partitions for /home /usr and /opt.

My question is: do I do a new install of Gutsy to root, after first backing up /etc/fstab, overwriting the old installation, and then replace the /etc/fstab with the backed-up version?
Then I can remove the newly created /home /usr and /opt from the new installation?
Of course I would back up my /home /opt and /usr partitions before doing anything.

Have I got this right?


I would say "no", unless you have some really special operational requirements that you didn't mention.  This sounds like an overly-complicated (and therefore fragile) approach to doing what you want to do.

Putting /home on its own partition makes great sense, and of course swap needs its own partition.  But why break up the rest of it?  Make a 6 or 8 GB partition for "/" and everything else but "/home" should be happy in there for another year or however long you're going to run it.

6GB = /
0.5GB = swap (unless you're a hibernating laptop that needs swap = RAM)
the rest of it = /home

Use the Alternate Install CD to set the mount points for these and any other partitions you want mounted in /etc/fstab, and it will write a new fstab for your new installation - no need to drag back in the old one from the prior installation.  Likewise with the Grub boot menu.  :guitar:

---

### Post by DrewB on 2007-10-08
Thanks for your response dabl,
I have a 100GB hard drive so I have, approximately, 10GB for root, 3GB for swap, 40GB for /home, 30GB for /usr and 10GB for /opt.

I read somewhere that it was a good idea to have separate partitions for /home, /opt and /usr so that's why I did it like that. However do think that its overly complicated so I will go to just having partitions for /home, / and swap.

So when I use the Alternate Install CD to do the new install of Gutsy Gibbon and I set mount points for /home, / and swap, will my current /home partition and data be left alone? While / will be overwritten?

Thanks
Andy

---

### Post by rsambuca on 2007-10-08
I agree with dabl.  For a regular user, there is virtually no reason to have all of these different partitions.  I personally don't even use a separate /home, although I have a separate partition for my music, videos, etc.

---

### Post by DrewB on 2007-10-11
I wish I'd never mentioned the partitions I have. How to partiotion the hard drive wasn't the point of my post. All I wanted to know was what would happen to my current partitions (in particular the /home partition) when I re-install the operation system and how to handle the re-install.

When I first installed Ubuntu I'd read that having separate partitions for your user data allowed for easier re-installs and or updates of the OS, without losing or disrupting your user data. However I can't find any documentation or advice to read on this before doing the re-install. I just want to know what to do, what will happen, the steps to take and precautions to make.
Thanks a lot

---

### Post by rsambuca on 2007-10-11
Hey, sorry!  We were just trying to make things easier for you down the road!

Anyways, to answer your questions:

If you are doing a simple re-installation and wish to use the existing partitions, you would select the "Manual Partitioning" option.  From there, you can point to your old /, /usr, /opt, /swap, and /home directories.  Just make sure you do NOT format the /home partition, and it will retain all of your old settings.  Most of the settings ***should*** be carried over, although sometimes there are minor hiccups with this.

Personally, I would consider making your / directory 20GB, a small swap, and the rest as /home.

---

### Post by rsambuca on 2007-10-11
And I forgot to add - make sure you backup any sensitive data first, just in case.  Problems with these simple re-installations are rare, but you never know.

---

### Post by DrewB on 2007-10-11
Ok, thats great! Thanks a lot for your help.

---

