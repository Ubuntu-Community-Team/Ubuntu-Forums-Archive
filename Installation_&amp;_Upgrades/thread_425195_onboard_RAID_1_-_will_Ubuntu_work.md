---
title: "onboard RAID 1 - will Ubuntu work?"
date: 2007-04-27
forum: Installation &amp; Upgrades
---

### Post by energy2spare on 2007-04-27
I have a WinXP desktop with an onboard RAID controller running my 2 drives in RAID 1. I cannot locate a Linux based RAID driver from the manufacturer. I tried installing Fedora Core 4 so I can dual boot but it complained about the RAID setup and would not proceed. 

I'm curious as to whether Ubuntu will work. Anyone have experience with installing Ubuntu on a RAID 1 set? The reason I ask is that I tried Ubuntu but got the following error:

/bin/sh: Can't access tty; Job control turned off

Before I go too far in trying to figure out what the error is, I'd like to find out if anyone's had experience with installing a dual-boot with RAID 1.

(My motherboard is a DFI LanParty 875 b)

Thanks!

---

### Post by Big Ed on 2007-04-27
I haven't had a dual-boot on raid, but I have a server running to disks on raid-1 that works good.  Your motherboard almost certainly does not have a true hardware raid.  

[http://linux-ata.org/faq-sata-raid.html](http://linux-ata.org/faq-sata-raid.html)


This is a good thread on setting up raid in Ubuntu Edgy:

[http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)

HTH,
Ed

---

