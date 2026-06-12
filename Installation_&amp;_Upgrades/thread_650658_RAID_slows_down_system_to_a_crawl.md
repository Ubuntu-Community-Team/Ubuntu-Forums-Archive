---
title: "RAID slows down system to a crawl"
date: 2007-12-26
forum: Installation &amp; Upgrades
---

### Post by user_of_gnomes on 2007-12-26
Hello,

I am trying to install Ubuntu 6.06 (Server / AMD64) on the following system:

AMD Athlon 64 +4000
Asus A8V-VM SE
512MB DDR RAM
300Watt Q-TEC PSU
1x 52x CD-ROM (IDE, Slave, channel 2)
1x 20.4GB  Maxtor 32049H3 (IDE, Master, channel 1) 
1x 15.4GB IBM-DJNA-351520 (IDE, Master, Channel 2) 

Hard drives check out fine; no SMART failure, no damaged sectors. 
PSU is on the low side, but I've seen systems function with worse. 

I followed the guide on [http://www.howtoforge.com/linux_software_raid](http://www.howtoforge.com/linux_software_raid) and redid the steps many times over with different configurations and hard drives, switched the IDE cables around but everytime I get to >  Now it is time to connect the partitions on hda and hdb and create the RAID1 arrays.

the system slows down to a crawl; the more I create, the longer it takes for the setup to do anything at all until it finally just stalls. 

I've never set up a RAID system before, not even using Windows.. Is there something I forgot to do? 

Looked around in the BIOS,saw an option under the Chipset configuration that could be changed to either IDE or RAID, didn't make a difference.

Jumpers are set to Master/Slave. 

HDD's are detected by both the BIOS and Ubuntu setup.

Memory checks out fine, so does the processor. Motherboard is brand new.

Advise is much obliged, have a good night.

---

### Post by user_of_gnomes on 2007-12-29
Still haven't figured it out..

---

