---
title: "Need a Partition help"
date: 2018-10-30
forum: Installation &amp; Upgrades
---

### Post by dpcloud on 2018-10-30
Hi am new to the forum, recently we bought new rack server from Supermicro the server has 2x2TB SATA HDD and 1x960GB SSD HDD, I need to install Ubuntu and am confusing myself to partition. 

sda 2TB 
sdb 906GB SSD
sdc 2TB 

I want to setup KVM and LVM for guest OS. Please advise. thanks in advance

---

### Post by TheFu on 2018-10-30
I would disconnect all the storage except the SSD and install Ubuntu server using LVM. Today, I would install 16.04 as some of the 18.04 issues are lingering that I'm not prepared to try to solve.  

Post installation, after all the patching, I'd reduce the / LV to be 25G on the SSD, give /home some amount and perhaps /var could use 25G. I'd leave probably 800G free, unallocated to any LVs on the SSD.  The VG would cover the entire SSD.

Then I'd setup the external disks with LVM+RAID1 into a different PV, different VG limited to the spinning disks.  Add new LVs for each planned VM. There are reasons for doing it this way.  I'd be careful to only star with 25G install LVs for each VM, then add more LVs where needed.  Don't allocate more storage than necessary anywhere.  
Wasted storage will be filled quickly and you haven't mentioned any backup methods yet.  Backing up using LVM-snapshot and rdiff-backup are fairly well understood.

What you do inside each VM is up to you.

---

