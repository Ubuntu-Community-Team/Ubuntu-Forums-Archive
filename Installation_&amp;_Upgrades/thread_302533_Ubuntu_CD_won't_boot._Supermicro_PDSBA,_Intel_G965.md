---
title: "Ubuntu CD won't boot. Supermicro PDSBA, Intel G965"
date: 2006-11-18
forum: Installation &amp; Upgrades
---

### Post by naxos on 2006-11-18
Hi Everyone,

  I am trying to install Ubuntu on a brand new Core 2 Duo
machine.  But none of the Edgy or Dapper CD's will boot.
Could anyone please shed some light on my situation.
  
  My motherboard is a Supermicro PDSBA.  It has an Intel G965
chipset, and also an Intel ICH8 SATA controlle.

  I am trying to boot from a Plextor PX-755SA SATA CD/DVD drive.
I have also tried booting from a SCSI CD-ROM with the same
results.  This motherboard has no parallel ATA connection.

  For the Server and Live CDs, I get the following boot messages 
and then a hang:

PCI: BIOS BUG #81[49435024] found
PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.
PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.
PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.

  When trying the alternate CD, in text mode, I see what looks
like normal USB controller/hub detection and then a hang.

  Fedora Core 6 will boot from CD just fine.  I also have
FC5 pre-installed on the hard-disk, and I could post the
dmesg from that install if it would be helpful.
  
  For reference, the FreeBSD 6.1 CD also refuses to boot, but
a Windows 2000 install CD boots just fine.
  
  Thank in advance,
  
    Lee

---

