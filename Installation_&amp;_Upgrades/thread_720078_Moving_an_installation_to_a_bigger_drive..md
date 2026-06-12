---
title: "Moving an installation to a bigger drive."
date: 2008-03-09
forum: Installation &amp; Upgrades
---

### Post by Hospadar on 2008-03-09
I have an ubuntu installation on an 80 Gb IDE disk, which I'm replacing with a 300 Gb sata disk.

I had some data on the 300 gb disk that I needed to keep (it used to house a different ubuntu installation) so what I did was (using gparted)-

-First I shrunk down the existing partition and moved it to the upper half of the disk.  it was only about 100 gig, so there was plenty of space left.

-I used gparted to copy over the / and /home partitions from the 80 gb drive onto the newly created free space on the 300 gb drive.

-I grew the /home partition that was copied over to fill up the free space from the original partition resize.

Once I get the copied installation running, I'm going to copy over the data I need from the old partition, and then delete that old partition.

So what I really need to know is what I need to do to make the copied over install work properly.  I assume that I can re-install grub and point it to the copied over / partition to take care of menu.list.  What I'm really wondering is if there is some easy way to re-set up the fstab to point to the correct partitions.  Is there any kind of tool like what the installer uses to set up fstab with the correct / and /home partitions?

---

