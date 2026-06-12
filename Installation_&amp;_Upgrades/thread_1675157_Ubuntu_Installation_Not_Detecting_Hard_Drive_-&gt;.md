---
title: "Ubuntu Installation Not Detecting Hard Drive -&gt; gSATA"
date: 2011-01-25
forum: Installation &amp; Upgrades
---

### Post by GreenPanda on 2011-01-25
Hey all, I'm trying to dual boot windows and ubuntu on a 1TB hard disk which is currently plugged into the gSATA port on my board. For some reason the installation is not detecting the hard drive. I'm going to plug the drive into the normal sata port, but I just wanted to know; is this normal? If it isn't, is there anyway to fix this?

---

### Post by Mark Phelps on 2011-01-27
I have an Gigabyte board and it has GSata ports as well as the "regular" SATA ports.  Are these what you are talking about?

If so, my guess would be that the installer does not have the driver needed to see these new SATA ports.

You could try installing using the Alternate CD.  It is able to handle RAID setups, so it might have the driver needed for GSATA ports.

---

