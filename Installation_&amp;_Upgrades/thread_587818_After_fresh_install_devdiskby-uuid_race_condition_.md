---
title: "After fresh install: /dev/disk/by-uuid race condition crashes Ubuntu?"
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by matthias_k on 2007-10-23
Hi,

so the nightmare called Ubuntu 7.10 continues for me - unfortunately. The problem: Every 2nd or 3rd boot, the kernel crashes with the error message that it can't find the file /dev/disk/by-uuid/<long-UUID> and spits out ATA failures.

Now, I always found it weird that Ubuntu treats my IDE hard drives as SCSI devices, addressing them using /dev/sdX files, but what's even weirder is that Ubuntu *changes* these device names from time to time, meaning my first hard drive and partition from which I boot (which should actually be /dev/hda0) is sometimes /dev/sda1 and sometimes /dev/sdb1. It has been this way since Edgy I think.

Now the first problem is that I have to address my disks in fstab by UUID, because the device names can change with each boot. The second problem is that (unlike with older Ubuntu releases), this does not always work, as stated initially: It looks as if there's a race condition between the kernel entity that creates /dev/disk/by-uuid and the kernel entity which tries to access these files to read from them.

So, does anyone have an idea how to fix this, because, I'm really not far from dumping Gutsy and reinstalling Feisty instead. Sorry, but I have never had this much trouble with an Ubuntu before, I'm really disappointed in its system unstability. :(

---

### Post by matthias_k on 2007-10-23
Anyone?

---

### Post by okey666 on 2008-03-02
I have a similar problem. My computer with any version of Linux on it (I have not tried Windows)  will only start up about 1 in 5 times. On Ubuntu the other times it displays the starting splash screen and then freezes. If I remove the splash it comes up with the same error. On other versions of Linux it complains about ATA hard drives not being available or something (I can't remember the exact messages.

---

