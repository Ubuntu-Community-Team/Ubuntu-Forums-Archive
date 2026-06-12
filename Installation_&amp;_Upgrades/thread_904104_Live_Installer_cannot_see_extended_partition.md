---
title: "Live Installer cannot see extended partition"
date: 2008-08-28
forum: Installation &amp; Upgrades
---

### Post by jbor7755 on 2008-08-28
I am trying to install Ubuntu 8.04 to my Dell XPS 1330.

I have installed Win XP on one primary partition at the begining of the drive.

I want a big extended partition in which I can install different flavours of linux (Ubuntu and Scientific to start with).

However the Ubuntu 8.04 x64 Live installer has no graphic representation of the partitions and has no ability to create extended partitions.

I stopped the install and went back to the live USB I'm using (created with Unetbootin), opened GParted and created an extended partition.

When I went back to the installer the new extended partition (254 GB) was not seen by the installer. Instead it sees 272881 MB of free space.

Ironically, on booting into XP the extended partition is recognised by disk manager.

How can I get the installer to recognise the extended partition?

Cheers

---

### Post by cariboo on 2008-08-29
The easiest thing to do is to do not partition your dirve before starting the installation. Delete any partitions you have created, then during the installation use the built in partitioning tool to manually create the partitions you need for Ubuntu. Then just create partitions as you go when installing other distributions.

Jim

---

### Post by jbor7755 on 2008-08-29
Thanks for the reply,

I know that's the easiest thing to do but I need to have an extended partition to give more flexibility later and the installer gave me no option to create one (I don't know why).

I think it would have been fine to use some of the free space and the swap and root would have ended up in the extended partition, but, to make sure, I created ext3 and swap partitions using GParted from LiveUSB and went back to the installer and installed to those partitions.  All seems to be working okay now.

Thanks again for your reply.

Cheers

---

### Post by jbor7755 on 2008-08-29
I spoke too soon.

Post installation I checked GParted again and found that the extended partition has been shrunk around the ext3 and the swap, leaving about 211 GB of unpartitioned space in between.  How can I install other distributions in an extended partition when this is happening?

Why won't the installer leave unallocated space in an extended partition?

---

### Post by jbor7755 on 2008-08-29
Correction... the 211 GB of space is between the Windows XP partition (primary) and the extended (containing Ubuntu, swap and some 7.88 GB free)

---

### Post by jbor7755 on 2008-08-30
Okay this is solved.  I had to use GParted from my live USB again and unmount swap before I could resize the extended partition to cover all the available space.

---

