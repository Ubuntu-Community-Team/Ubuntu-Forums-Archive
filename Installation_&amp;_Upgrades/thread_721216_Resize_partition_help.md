---
title: "Resize partition help"
date: 2008-03-11
forum: Installation &amp; Upgrades
---

### Post by ftornell on 2008-03-11
Hi,
I have a Laptop (Lenovo T61p) with Windows Vista installed on it!

Then I installed Ubuntu 7.10 Desktop edition and shrunked Vista partition and made a new one for Ubuntu.

Partition 1 = 85 GB Vista
Partition 2 = 15 GB Ubuntu

Now I want to resize the Ubuntu partition to 50 GB (make it bigger) so the Vista partition gets smaller to about 50 GB. Is it possible or must I reinstall both os?

Help me out please!

---

### Post by FutureIsLinux on 2008-03-11
You are going to have to download a Gparted LiveCD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php) or another liveCD with the Gparted tool (NOT the newest ubuntu release, its bugged so dont try use that). Start by shrinking the windows partition to 50GB then you may have to Move the SWAP partition back to the new end of the windows partition (so you can resize the Linux partitions without it being in the way), then resize the linux partitions. Hope this has helped.

---

### Post by AndyCee on 2008-03-11
If Vista can safely shrink its own partition, then using the same partition manager should be safe for Vista and also should be safe for extending the Ubuntu partition (as no memory on the Ubuntu partition is being overwritten).

That said, I used 'should' twice as I haven't used the application before. Remember to always back up before changing a partition.

Here is some info with explanations of the process
[http://www.bleepingcomputer.com/tutorials/tutorial133.html#shrink](http://www.bleepingcomputer.com/tutorials/tutorial133.html#shrink)

---

### Post by dcstar on 2008-03-11
> **FutureIsLinux said:**
> You are going to have to download a Gparted LiveCD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php) or another liveCD with the Gparted tool (NOT the newest ubuntu release, its bugged so dont try use that). Start by shrinking the windows partition to 50GB then you may have to Move the SWAP partition back to the new end of the windows partition (so you can resize the Linux partitions without it being in the way), then resize the linux partitions. Hope this has helped.

The Windows partition can be shrunk without a CD, just use the Partition Editor (gparted) and unmount it before resizing.

The Ubuntu Live CD's Partition Editor may need restarting after each completed operation, but it is quite usable for expanding the Linux partition.

---

