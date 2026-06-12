---
title: "OS X/MacBook Air: Can I install Ubuntu onto an external SSD?"
date: 2015-05-26
forum: Installation &amp; Upgrades
---

### Post by Bob_Emerson on 2015-05-26
I have an early 2014 MacBook Air laptop that has very little space left on it. I have an 450 Gig external SSD drive and a suitable cable to connect it to my laptop via a USB3 port. I have managed to get Ubuntu to boot from the external SSD drive in "try" mode but really want it to "install" onto the external drive. I can get as far as the partitioning screen on the installer by do not understand how best to partition the drive? I have read and re-read the appropriate forum threads using the "search" function but have only ended up confusing myself. 

How should I partition the external drive?

Thanks in advance for all help and suggestions. Bob

---

### Post by ubfan1 on 2015-05-26
The first thing to be aware of is the lack of TRIM on most (all?) USB3 external enclosures.  Your SSD performance will degrade much faster than if it were installed internally to a regular SATA port.  I have set up several such SSDs, but haven't used them much.  I treated them like flash stick setups, moved the frequently used directories into ram (search for optimize flash in the forum or in askubuntu).  I do not use swap on my SSDs, and use the guest session whenever possible to avoid many of the Desktop file updates you'd normally get.  I like to make room for at least two root partitions (30G apiece) so I can test out a new release without jumping off the cliff).  Don't know if this is a UEFI setup, I assume so, so a 300M EFI partition (assuming you can boot off the drive).  The rest may be a big data partition you can mount under your home directory for your files (which may be shared between the two different root directories since all the desktop specific files have their own root specific home directory.

---

