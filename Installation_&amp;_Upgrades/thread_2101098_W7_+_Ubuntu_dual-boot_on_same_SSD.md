---
title: "W7 + Ubuntu dual-boot on same SSD?"
date: 2013-01-03
forum: Installation &amp; Upgrades
---

### Post by blackshine on 2013-01-03
Hey,

have an SSD as my primary boot drive running W7 64-bit.
Would like to install Ubuntu 64-bit on the same SSD and have dual-boot.

Is the Wibu installation from within W7 the best approach here?
Or should I boot install Ubuntu from DVD? Choosing the latter method, do I run into any problems or can I get a smooth dual-boot install this way?

Cheers!

---

### Post by darkod on 2013-01-03
I would never call wubi inside windows a good approach. It was developed as a quick try, not as long term install. So i wouldn't count on it. Not to mention that any issues are more difficult to troubleshoot since it's a virtual machine and not a proper installation.

I can't see why you wouldn't be able to get a smooth dual boot if you install ubuntu properly on its own partition. I have a ssd dual boot, that's not uncommon these days.

Potentially other hardware can give you issues sometimes, but dual booting on a ssd is not an issue by itself.

---

### Post by nwalkey on 2013-01-03
I found wubi to work very well and likely would have stayed with it if I didn't want to increase space on my ubuntu partition and swith from 12.10 to 12.04. That being said, if you are installing from a new machine or don't care about losing your current windows partition, definitely install them separately. I haven't even bothered to reinstall windows after reinstalling ubuntu. Just set up your partitions appropriately and you'll be fine. I set 8gb for swap, 90gb for ubuntu (mounted at /) and the rest for windows(currently empty). Hope all goes well for you.

---

### Post by blackshine on 2013-01-03
Thanks for the quick responses!
I'll do it the proper way then, just fingers crossed it won't mess up my current active Windows partition as I need it working for a couple programs, unfortunately :/

---

### Post by blackshine on 2013-01-03
Okay, I'll hijack my own thread for another question, ha!

When creating the partitions for Ubuntu within the installer, can I point the home partition to a HDD instead of the SSD? How would I do that? Or does that logically not work?

---

### Post by nwalkey on 2013-01-03
You can definitely set your /home to be on a different hard drive and you won't experience any problems. I don't know that effects performance though. I know that many programs store their settings and files in the home folder so you might have more frequent read/writes to the slower hdd.

---

### Post by darkod on 2013-01-04
Yes you can, but you have to use the manual installer (Something Else). The auto method creates only / and swap, and selects their sizes according to the unallocated space you left it.

With manual install you can select the exact partition sizes, their location on any disk, and the bootloader destination (note: it should be the MBR of the disk you will use to boot from, not a partition).

Putting /home on the hdd will have some slower effect but I can't tell you how much exactly either.

One option would be to create /home on the ssd too, but not use it for any large files. That way you can make it small because ssd disks are still small in size.
During the manual install you can create one large partition on the hdd and use any mount point for it that you like, for example /data, and keep all large files there.

You have many options, it all depends how you will decide to set it up, and whether other people will use the computer and know where to find the data and not keep large files in their home folders.

---

### Post by blackshine on 2013-01-04
Okay, will give it a shot! :)

---

### Post by nwalkey on 2013-01-04
darkod, do you know of a way to install specific programs to non-default locations using apt-get/software centre?

---

### Post by darkod on 2013-01-04
> **nwalkey said:**
> darkod, do you know of a way to install specific programs to non-default locations using apt-get/software centre?

Nope, haven't got that far.

---

### Post by Mark Phelps on 2013-01-04
I didn't catch if you already set aside space on your SSD for Ubuntu, but if you haven't, then do NOT use the Ubuntu installer to shrink Win7.  That risks corrupting the Win7 boot loader and leaving it unbootable.

Instead, use the Win7 Disk Management utility to do the shrinkage -- but do not create a new partition.

Create the Ubuntu filesystem partitions when doing the installation by selecting Something Else.

---

