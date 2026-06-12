---
title: "raid installation"
date: 2007-09-01
forum: Installation &amp; Upgrades
---

### Post by scalextric on 2007-09-01
Hi there, new to Ubuntu and trying to install 7.04 from a liveCD and acheive a dual boot Windows/Ubuntu setup.
Have Windows XP completely filling  a RAID 0 partition created by two 80GB SATA HDDs and an Adaptec PCI card.
When installing Ubuntu from the CD I get to the partitioner and see the following options
-- Automatic
   --  SCSI 80GB HDD A
   --  SCSI 80GB HDD B

-- Manual

'Automatic' and drive 'A' is selected by default, but Im concerned if I follow that, it will damage my RAID 0 partition for Windows.  
Little confused as to why Ubuntu sees the 2 x HDDs and not the RAID controller... the RAID controller boots to BIOS before the live CD loads Ubuntu....:confused:
Have no experience with partitioning HDDs in any OS and anything I tried reading on the MS help pages frankly left me more confused than when I started:(

Hopefully someone can decypher my setup and get me to a solution withoud destroying my Woindows setup, thanks!

---

### Post by Pumalite on 2007-09-01
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

