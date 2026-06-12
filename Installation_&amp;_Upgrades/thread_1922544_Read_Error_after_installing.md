---
title: "Read Error after installing"
date: 2012-02-09
forum: Installation &amp; Upgrades
---

### Post by HugoStiglitz on 2012-02-09
Hi guys,
 
I have been trying to install ubuntu on to my HP PAvillion dv6500.  It goes through the installation no problem but when I boot from the HDD it gives 'Read Error'.  Is this something to do with the HDD being a SATA drive?  I have tried Zorin too with the same result.
 
I can boot to the Live CD image no problem but I am stumped on this one.  BTW I am a relative linux newbie although not new to computers if that makes sense.

---

### Post by sikander3786 on 2012-02-09
Welcome to the forums. :)

"Read errors" don't sound great as most of the time, they point us to the failure of HDDs. First of all, you should check your HDD against any bad sectors. There are several different methods of doing this.

You can check in the Bios settings if 'S.M.A.R.T' reporting is enabled. If it is, it might be telling you that the disk is failing or also if it is healthy.

If that isn't possible, from an Ubuntu Live CD/USB, you can run the default disk manager and scan your HDD for bad sectors.

Or you can also go to your HDDs manufacturer's website and download the diagnostic tools.

Can you hear any sounds like 'click, click' from the HDD?

You might also want to change the HDD SATA cable and try booting Ubuntu again but that won't be of much help, I guess.

---

### Post by HugoStiglitz on 2012-02-09
The HDD is relatively new, my first thought was a failure of some sort but I checked it in the BIOS and all ok.

---

### Post by HugoStiglitz on 2012-02-10
Any ideas fellas?

---

### Post by travitar on 2012-07-16
I fought with this problem today and came to a solution for my case.  I had a perfectly functional Windows Server running and decided to upgrade to Ubuntu 12.04 server.  After installing I ran into this same "Read Error" upon boot.  I tried disconnecting driver physically, installing to different drives and even installing Ubuntu 12.04 desktop.  All resulted in the same "Read Error" problem.

What finally fixed it for me was either disabling Quick Boot in the bios or telling my bios to initialize the PCI express slot first (even though I'm only using on-board).  I made those two changes an a whim at the same time and it worked.  I'm not sure which of those two actually fixed it.

For reference my motherboard is a Gigabyte GA-Z68M-D2H with an i5-2500K cpu and 16gigs of ram.  I tried both a Seagate and a WD drive as boot drives.  The drives do not have problems.

---

