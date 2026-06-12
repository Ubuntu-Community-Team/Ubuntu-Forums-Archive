---
title: "Install onto an SD card"
date: 2011-09-29
forum: Installation &amp; Upgrades
---

### Post by jdb91 on 2011-09-29
I know there are similar posts, but I can't find an answer that works.  I want to install the bulk of Ubuntu 11.04 onto a 16gig "high speed" (apparently) SD card that I'm going to leave in the laptop and mount the NFS drive to share with Windows (needed for TV card etc.)

There is about 12 gig empty partition on the main HDD, which I will need to use to boot Ubuntu as the SD doesn't appear to be bootable via BIOS (but is recognized by Ubuntu installer).  What do I need to put in the 12 gig partition? I.e. /boot? / is too big too fit and the installer crashes at the end.

I mainly want it on SD to benchmark speed.

Cheers,
Joe

---

### Post by oldfred on 2011-09-29
You should be able to fit all of / (root) in your 12GB. Install is now about 4.4GB and I often suggest 10 to 20GB for / when data or /home is stored elsewhere. My typical install with lots of applications is about 6GB but I have all my data elsewhere.

I have not tried it but /boot should work on hard drive as that has grub's files & the kernels (like a minimal install). The rest is loaded after boot and should see the system, just not sure when partitions are loaded.

I normally suggest keeping the system on one device including grub2's boot loader, but that is for reliably, so if one drive fails an install on another may still work. But if you cannto boot SD then you have to do a work around.

---

