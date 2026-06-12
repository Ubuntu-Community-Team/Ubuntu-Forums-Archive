---
title: "Ubuntu install problem"
date: 2005-03-17
forum: Installation &amp; Upgrades
---

### Post by davidwashere2003 on 2005-03-17
I'm trying to install Ubuntu on a comp with the following specs:

-ASUS P2B-L motherboard
-PII 450MHz CPU
-128MB SDRAM
-WD Caviar 22000 (2GB) Hard drive
-ATI Mach64 VT video card
-Artech DHM-G48 just a 16x DVD-ROM
-Intel EtherExpress 16TP LAN adapter

-Had RAM trouble. Switched RAM and install started working.

-Had problem with detecting NIC, but I just selected the Intel EtherExpress 16TP LAN adapter from a list and kept on truckin.

-Partition went through okay... part went to ext3 and another to swap.

-Can't get past the Install Ubuntu step, it just keeps giving the following error:

"The debootstrap program exited with an error (return value 2).
Check /var/log/messages or see virtual console 3 for the details."

I got to /var/log, but have no idea what to do once I'm there. 
And I don't know what virtual console 3 is... I've checked the Howto's and some other threads but can't seem to get any info on where to go now. I'll mess with hardware for now.

Any help is appreciated.
Thanks.


-----
Problem seems to be solved.

Switched the Artech DHM-G48 with a Samsung SC-148 (48x) CDROM.
And removed the Intel EtherExpress 16TP LAN adapter.

Attempted install and it went through just fine.

Must have been the slower DVDROM or the NIC.

Will try installing a 3COM EtherLink 10/100 PCI NIC once it reboots.

Seemed to have answered my own question.
Should be able to follow the guides for what needs to be done from here.

Thanks anyway.

-------

The WD Caviar is too small, I've run out of space.

3COM NIC is working fine. Did updates.

Thought I had read that Ubuntu could fit on 1.8GB, maybe that'd require some cutbacks. Not sure how to do this.

Switched hdd temporarily with a Seagate Medalist 6531 (6.4GB) hopefully that'll work.

---

### Post by Buffalo Soldier on 2005-03-28
How's your installation so far? Sorry for the late reply. Anyway, have you gone to this site? [http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html](http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html)

---

