---
title: "SATA port multiplier on 8.04"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by drl2 on 2008-04-29
I've got a clean install of 8.04 up and running fine on a single 200G drive (/dev/sdc) on a machine I'm going to use as a media server.  I've added 2 500G drives connected to a Sil3112 card and those are configured fine - they showed up automatically as /dev/sda and /dev/sdb, and I configured them as RAID 1.  I want to add a similar pair of drives (with room for more in the future) in an external enclosure; the machine also has an Addonics Sil3124 controller connected to one of their port multipliers.

I was under the impression that under newer kernels the multiplier was supported and both drives should be recognized, not just the first one on the PMP that the BIOS recognizes.  Unfortunately this isn't happening - Ubuntu sees /dev/sdd but no /dev/sde.  Is there some further configuration I need to do?

---

### Post by drl2 on 2008-05-05
<Bump>

Anybody?  Is there a different distribution I might have more luck with?

---

### Post by drl2 on 2008-05-13
Well, as far as I've been able to tell, the kernel I'm running is supposed to have the PMP support in it, but the drives are still not being recognized.  Have looked & asked in various forums with no results.

<Sigh> I suppose it's time to abort yet another attempt to use Linux and scrape up another copy of XP and just take the performance/Microsoft-tax hit in the name of getting this working.

---

### Post by blackoper on 2008-05-25
I've run into the same problem in 8.04. I would try installing Fedora 9 and see if it works in there. I think it's the kernel version of hardy that is causing you the issue. Ubuntu is kernel 2.6.24 and fedora 9 is 2.6.25 so see if that makes a difference

---

### Post by theraidbox on 2009-07-14
Consider using a hardware port multiplier solution instead of the software raid implementation of SATA controllers and port multipliers using Silicon Image chips. A 4x1 eSATA/USB Hardware Port Multiplier (HPM) that is OS independent and will work with any eSATA port is an alternative solution. The 4-port SATA integrated HPM with an Oxford OXUFS936QSE chipset uses hardware raid technology.
 
RAID mode selection is done using a rotary switch and setup is completed by pressing a raid setting button. Once configured all is needed is to connect the HPM to your system via USB 2.0 or eSATA and detect, partition & mount the RAID volume. 
RAID mode supported are FAST2 (2 drive RAID 0 Striping),, SAFE2 (RAID1 Mirroring), SAFE FAST (RAID 1+0 Mirrored Stripped), BIG 2 (2 drives Concatenation), FAST4 (4 drive RAID 0 Striping), BIG 4(4 drives Concatenation), RAID 1+0, RAID 5 over 4 drives, or RAID 5+S. 
 
Connecting the HPM to onboard SATA ports on the motherboard is possible by using 2 eSATA ports PCI slot mounting bracket with two eSATA connectors to convert internal Serial ATA to eSATA.
 
2TB, 3TB, 4TB, 6TB & 8TB Turnkey RAID solutions utilizing the 4x1 eSATA/USB Hardware Port Multiplier (HPM) are available at
[https://www.theraidbox.com](https://www.theraidbox.com)
 
The way software RAID works using SI controllers and port multipliers (PM) is that, you use mdadm to see and configure as a raid volume all 5 drives connected to the PM. If the PM is connected to non-PM aware controller card (legacy) it will only detect one drive out of the 5.
 
But using a Hardware Port Multiplier which uses an integrated hardware controller, the raid setup is done on the HPM itself. So once you connect it to a SATA port, it will be seen as a single RAID volume.

---

