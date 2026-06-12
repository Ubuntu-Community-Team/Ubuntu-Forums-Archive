---
title: "Installation probs on machine with no OS"
date: 2008-01-30
forum: Installation &amp; Upgrades
---

### Post by CraZYboYs on 2008-01-30
I'm trying to load Ubuntu 7.10 on a Gateway with no OS.  It's PIII, 730MHZ CPU, 512mb RAM, 20GB hard drive.  We purchased from the local university which removed the old OS.  I tried a disk that we were given with Ubuntu on it and nothing happened, CD went in and then the cursor just sat there.  So, thinking maybe it was a disk issue, I downloaded and burned another copy.  Still nothing, just a big black screen and my flashing cursor.  Any ideas?  I'm new to Linux, so ANY help would be appreciated.  Thanks!!

---

### Post by njparton on 2008-01-30
Can you confirm that the ISO was _extracted and burnt_ to the CD correctly? Not just copied to the CD and burnt? (if you browse the CD on another computer you should see a series of files not just the ISO file).

If you think it's the hard drive, download "super F disk" boot from that and use it to clear the MBR and delete any lingering partitions from the hard drive.

Ubuntu installer can be quite sensitive to dodgy hard drives in my experience.

---

### Post by CraZYboYs on 2008-01-30
I put the disk in this machine (separate one from the Gateway) and I have the "Disk Tree" pop up where I can install things.  I downloaded, extracted and burned the super F disk to CD and tried that and now I'm getting a "cannot detect media" error.  Still nothing on the Ubuntu disk.  

Other suggestions?  THANKS!

---

### Post by CraZYboYs on 2008-01-30
problem solved!  There was a master/slave set up I wasn't aware of.  Working great now!  Thanks for your help!

---

