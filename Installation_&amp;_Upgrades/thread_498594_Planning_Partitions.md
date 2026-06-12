---
title: "Planning Partitions"
date: 2007-07-11
forum: Installation &amp; Upgrades
---

### Post by SPr on 2007-07-11
Hi,

I've decided to dump Windows and use Linux exclusively (I've not booted Windows for 6 months now) :) so before I go ahead and create something completely impractical I thought I'd ask for opinions.

I have an 80 GB internal HDD which I figure wants partitioning like this:
hda1 : / 		15 GBs
hda2 : /home		roughly 40 GBs
hda3 : /swap		1 GBs
hda4 : guest OS.	20 GBs

I have 757 MBs of RAM so a swap partition size of 1GB should be fine.

I would like the guest OS to have 20 GBs which I suppose would be ample for trying out new (to me) Linux desktop distros.

I upgraded Edgy to Feisty rather than installing Feisty from scratch and / currently uses 5.6 GBs so 15 GBs is more than sufficient.

Which leaves the rest of the HDD for hda2 which would be over 40 GBs.

Where would /swap be best placed? Where I put it? Between the / and /home partitions? Or put it on my external USB HDD? Would it really matter where it went? I've been reading about positioning the /swap partition for low read/write times and I've not really understood much of what was said. Hmmm... with a modern HDD does the distance the read/write heads travel make any significant slow down?

I would also be interested hearing how other people here would partition my HDD for themselves and why they'd choose that set up.

---

### Post by confused57 on 2007-07-11
Good info here on partitioning:
[http://www.users.bigpond.net.au/hermanzone/p17.htm#help_on_partitioning](http://www.users.bigpond.net.au/hermanzone/p17.htm#help_on_partitioning)
[http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by dabl on 2007-07-11
The root partition, "/", probably does not need to be larger than 8 or 10GB. The most I've seen it grow to is about 5GB, so there's a margin of safety if you set it to 10GB.

Two cents' worth. :)

---

### Post by SPr on 2007-07-11
> **confused57 said:**
> Good info here on partitioning:
[http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)


Now, that link is the goods :) I missed it when I searched so thanks for pointing it to me.

Dabl, thanks for your reply. I'll cut / down 10 GBs. I guess 15 is a little extravagant :)

---

