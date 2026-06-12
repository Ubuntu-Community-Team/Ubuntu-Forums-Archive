---
title: "Custom partitioning 10.04"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by linuxonbute on 2010-05-03
I am building a new machine on which I want to install 64bit 10.04.

It will be replacing another box so I will move the files I need off the old one which are on a separate home partition.

I believe that the default install for 10.04 is ext4 over lvm but have never used either.

Before I start I wonder if I can keep home on a separate lvm to the rest of the system. I intend to have about 300 gig for the rest of the system and start with 500 gig on /home.

Can I do this and, if I add more discs later can I assign them to the main system or /home as I want at the time or is that not how it all works?

---

### Post by oldfred on 2010-05-03
I think it is Fedora that uses LVM as a default. I have not used LVM and do not know much about it.

I have multiple root directories as I want a clean install with every update every 6 months. So I have previous, current & a beta all as root partitions and alternate current & previous. I moved /home to separate 100GB partition when I converted to Karmic but then moved almost all data out into a data partition. My /home uses about 1GB of the 100GB as everything is in /data. My root install is about 5-6GB so you do not need a large root partition if you have a separate /home.

---

### Post by srs5694 on 2010-05-03
Ubuntu definitely does *not* use LVM by default. In fact, I just did an Ubuntu 10.04 install to an LVM a couple days ago, and the installer was brain-dead enough to not install the lvm2 package to the LVM-based installation, with the result that the system wouldn't boot until I manually installed that package myself.

By "separate LVM," I'm going to assume you mean a separate logical volume, since there'd be little point in installing /home and root (/) on separate volume groups. In fact, let's back up a bit: There are three important data structures in LVM:


[list]
[*]**Physical volumes** -- These normally correspond to partitions, although you can use whole unpartitioned disks or RAID volumes as physical volumes.
[*]**Volume groups** -- These are collections of one or more physical volumes, which form a single pool of disk space that can be allocated as you see fit. Volume groups can be thought of as being very much like filesystems.
[*]**Logical volumes** -- These are data structures inside volume groups. They can be used like partitions (they hold filesystems or swap space), but they can be manipulated much like files in filesystems (grown, shrunk, added, deleted, etc.), without concern for where each one begins or ends, where free space exists in the volume group, etc.
[/list]


If you want to install Ubuntu to an LVM, you can, but you'll need to set it up manually before you install Ubuntu. (You can install the lvm2 package to the DVD version of the installer and then set it up with the text-mode tools, or add the system-config-lvm package and do it with a GUI. As noted above, you'll need to manually add lvm2 to the installed system.)

To proceed with your questions, yes, you can separate root (/) from /home in an LVM configuration. Doing so will give you the advantages of separating them on different partitions. If you add a new disk in the future, you can configure it as a physical volume, add it to a volume group, and then expand one or more existing logical volumes to occupy the new space, or create new logical volumes to fill the new space.

If you decide not to use LVM and you add a new disk, you'll need to either move data to the new disk and reconfigure a mount point, or mount the new disk at some point in your directory tree and use it from that space -- for instance, you might mount it at /home/yourname/extra and then put some files in that directory. This type of solution can usually work fine, but it's obviously more limiting than directly increasing the size of /home would be.

---

### Post by linuxonbute on 2010-05-04
Great, thanks guys.

I had read in 'Linux Format' ( a UK Mag ) that it did use by default ext4 over LVM which was the reason for my concern as I had never used it before. I thought that I would do a custom install, doing partitioning manually as I normally do, if there was going to be a problem as I always put /home on at least it's own partition or even a different disc.

So I think i will look into LVM a bit more so I can get to grips with it as there is no urgency in setting up the new machine. I have already backed up more than I need from the old one to a USB disc anyway.

thanks again,
Norman

---

