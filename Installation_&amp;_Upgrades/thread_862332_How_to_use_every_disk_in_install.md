---
title: "How to use every disk in install"
date: 2008-07-17
forum: Installation &amp; Upgrades
---

### Post by know-it-some on 2008-07-17
I have a machine with four 750 gig drives.  I want to install heron server, using all four disks as if they were one huge 3TB disk. The machine does not have a separate RAID controller and during install I am forced to choose one of the four disks to partition.  How to accomplish creating one giant volume?  Thanks!

---

### Post by know-it-some on 2008-07-18
It looks like what I want to do, since I do not have a RAID card available is set up all four of my disks to be a part of one large volume group.  I am trying to do this during the partitioning section of the install.

To do so I choose 'Guided with LVM' then select the first disk. The installer divides up the disk for me and creates a /boot partition and an LVM partition.  It also creates to volume groups, one for / and one for swap.

Then, I chose 'Go Back' so I can go back and configure the LVM. All this seems to consist of is activating the one volume group that is found and then I write changes to disk.   When the OS install is complete, vgscan doesn't find any volume groups.

What could I be doing wrong?  Is there a way to add all disks to a volume group during the server install?  Thanks!

---

### Post by jimv on 2008-07-18
Never done it, but here's a how-to:

[http://www.debuntu.org/how-to-install-ubuntu-over-lvm-filesystem](http://www.debuntu.org/how-to-install-ubuntu-over-lvm-filesystem)

---

### Post by Pumalite on 2008-07-18
Here is something to read:
[http://www.howtoforge.com/perfect_setup_ubuntu704](http://www.howtoforge.com/perfect_setup_ubuntu704)

---

### Post by know-it-some on 2008-07-23
> **Pumalite said:**
> Here is something to read:
[http://www.howtoforge.com/perfect_setup_ubuntu704](http://www.howtoforge.com/perfect_setup_ubuntu704)

This tutorial doesn't really apply to this topic.  I was asking how to set up LVM during install, but this tutorial doesn't opt for LVM at all:

[http://images.howtoforge.com/images/perfect_setup_ubuntu704/12.png](http://images.howtoforge.com/images/perfect_setup_ubuntu704/12.png)

But that's okay.  I am installing a Raid card and I am going to unite the drives in a RAID-0 config so I no longer need the LVM help.

---

### Post by know-it-some on 2008-07-23
> **jimv said:**
> Never done it, but here's a how-to:

[http://www.debuntu.org/how-to-install-ubuntu-over-lvm-filesystem](http://www.debuntu.org/how-to-install-ubuntu-over-lvm-filesystem)

This is a good LVM article, thanks!

---

### Post by louieb on 2008-07-23
> **know-it-some said:**
> But that's okay.  I am installing a Raid card and I am going to unite the drives in a RAID-0 config so I no longer need the LVM help.

Just wondering do you really want to use raid-0. You realize if one drive goes bad you will loose the data on the other drives.  

[http://en.wikipedia.org/wiki/Standard_RAID_levels](http://en.wikipedia.org/wiki/Standard_RAID_levels)

---

### Post by know-it-some on 2008-07-24
Thanks for looking out for me.  I am set on RAID 0.  I want the performance of striping without the overhead of parity.  The server will be participating in a hadoop cluster so not redundancy is really required. We'd rather have the extra space!  Thanks again.

---

