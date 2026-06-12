---
title: "Unbuntu installer failed to partition my hard drive - help please?"
date: 2007-05-03
forum: Installation &amp; Upgrades
---

### Post by pthow on 2007-05-03
I have previously installed Edgy on my five-year-old laptop.  But even the standard installation of Ubuntu seems a bit heavy for this old machine, so I tried to switch to Xubuntu, and somehow managed to mess up the configuration of X.  When Fiesty came out, I decided to do a clean installation: upgrading and solving my display problem together.

The live CD boots, and does indeed see my hard drive, in the read-only mode however.  And the installation program would quit at the step of re-partitioning, saying that I don't have the privilege to access the volume.

I tried to run gparted using the root terminal.  The volumes are still read-only.

But apparently the partition table is messed up already, and I can't boot from the hard drive anymore.

Help please?

AMD Athlon (?) 1000+
384 Mb of ram
The laptop is an ASUS N2D.

---

### Post by dannyboy79 on 2007-05-04
> **pthow said:**
> I have previously installed Edgy on my five-year-old laptop.  But even the standard installation of Ubuntu seems a bit heavy for this old machine, so I tried to switch to Xubuntu, and somehow managed to mess up the configuration of X.  When Fiesty came out, I decided to do a clean installation: upgrading and solving my display problem together.

The live CD boots, and does indeed see my hard drive, in the read-only mode however.  And the installation program would quit at the step of re-partitioning, saying that I don't have the privilege to access the volume.

I tried to run gparted using the root terminal.  The volumes are still read-only.

But apparently the partition table is messed up already, and I can't boot from the hard drive anymore.

Help please?

AMD Athlon (?) 1000+
384 Mb of ram
The laptop is an ASUS N2D.


well what would you like help with? do you want to somehow save your edgy install so you can perform an upgrade? or do you want to do a fresh install? 

if you want to do a upgrade, then we need to straighten out your partitions issue so you can boot into edgy. can you please boot to a live cd and provide me the results of

sudo fdisk -l

and along with that info, please tell me what is on each partition so I can further help you.

if you just want to do a fresh install, i would strongly suggest using the alternate install cd for xubuntu as it's not graphics based and normally doesn't have any issues with it. if you still want to use the live cd adn the installer is failing to partition your drive, I suggest just booting into a live cd and using gparted to wipe out your drive and leave it unallocated, then the installer should work. let me know the info I request if you want further help or let me know how it goes otherwise. sorry no one got back to you sooner.

---

### Post by zazen666 on 2007-05-07
I would try the live cd of Gparted. I had success with that

---

