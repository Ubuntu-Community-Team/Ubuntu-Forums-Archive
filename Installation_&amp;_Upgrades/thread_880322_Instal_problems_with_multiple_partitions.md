---
title: "Instal problems with multiple partitions"
date: 2008-08-04
forum: Installation &amp; Upgrades
---

### Post by Totenglocke on 2008-08-04
I have three partitions, one with Vista, one with XP, and a new 30 gig partition for Ubuntu.  I've used Ubuntu as the only OS on another laptop before and everything went great.  However, I can NOT get Ubuntu to install to the partition I want.

Using "guided - largest continuous free space" gives me a "partition too small" error (I wasn't aware that 30 gigs was small, so this is news to me).  I'm forced to use manual, I set 1 gig for a swap file and the rest for my / partition and proceed with installation.  Once it tries to format / install though I get an error saying that the partition can't be formatted.  Why?  It's currently fat32.  I love Ubuntu so I'm rather frustrated that I can't get it to install on this system.  Any ideas?

---

### Post by spin2cool on 2008-08-05
Try using the GParted Live CD to format the partition before running the installer.  What happens then?

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by coffeecat on 2008-08-05
> **Totenglocke said:**
> Using "guided - largest continuous free space" gives me a "partition too small" error (I wasn't aware that 30 gigs was small, so this is news to me).

I think you've misunderstood what's happening here. If you're getting this error, there must be a small amount of unallocated (unformatted) space on the drive. This is what the installer is referring to, not the 30GB fat32 partition.

Is that the Ubuntu live CD you're using (not the alternate)? If so you don't really need the Gparted live CD. Boot up with the Ubuntu CD and go to System > Administration > Partition Editor (this **is** Gparted, albeit an earlier version) and see what that has to say about your partition layout. I think you'll find your two Windows NTFS partitions, the fat32 partition and some empty space. Simply select the fat32 partition for deletion and then click on 'Apply'.

You should now be OK to select 'guided - largest continuous free space' in the installer.

However, if the free space is not continuous, if there's more than one piece of free space sandwiched between partitions, post a screenshot of the Gparted window and someone can advise you what to do next.

---

### Post by Totenglocke on 2008-08-07
I'd used gparted before, and even using gparted there is an 8 MB chunk at the end of my drive that I can NOT get to merge with another partition, my only option is to leave it free or make it an 8 MB partition.  Any tips?

---

