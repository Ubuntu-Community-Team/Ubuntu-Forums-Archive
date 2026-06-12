---
title: "GHO Image and VirtualBox on Ubuntu 8.10"
date: 2008-11-23
forum: Installation &amp; Upgrades
---

### Post by HishamN on 2008-11-23
Hi,

I took full image for my ex windows partition using Norton Ghost.
My image size is 13GB.

I created VirtualBox on Ubuntu named XP and I created two IDE HD.
One for the image (restore my GHO image)
Second I putted the GHO image to restore it (After successed restore I will umount it)

The problem is I have floppy image for ghost bootable disk and it booted successfully and I can see my GHO but when I try to choose and restore it I received error message that I need new Ghost version (I think because I toke my Image with new ghost version than the ghost bootable disk image.

Also if I try to boot using WinTools (which I used to create the image) it hang on loading cdrom driver!

Please tell me how can I restore my GHO to VirtualBox?

Thanks

Regards

---

### Post by HishamN on 2008-11-24
Any help please

---

### Post by HishamN on 2008-11-26
Solved

---

### Post by eaidoido on 2008-12-25
explanation?

---

### Post by HishamN on 2009-01-12
I created 3 partitions

one on my laptop (free space)
2 partition on a external HD (one has fresh xp installed and the other has GHO image)

these partiton's are conifigured to be on VirtualBox as guest OS (XP)

so I restored the GHO to the free space from the guest OS then I reconfigured VirtualBox to has one partion (Restored partiton) and it's worked.

Regards

---

