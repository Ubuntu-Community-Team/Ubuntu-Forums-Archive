---
title: "Installing Ubuntu 10.10 Server 64bit  asking for ISCSI volumes"
date: 2011-02-01
forum: Installation &amp; Upgrades
---

### Post by c4rdinal on 2011-02-01
Hi Everyone,

I have a problem hope you can help me. I'm trying to make a fresh install of Ubuntu 10.10 Server 64bit but is stuck with the Partitioning Disk part and Ubuntu 10.04 LTS provides the same error.

The installation wizard gives me a menu:

!! Partitioning disks
This menu allows you to configure iSCSI volumes
iSCSI configuration actions
      Log into iSCSI targets
      Finish
<Go Back>


I'am tried RAID 5 or 10 using my Intel motherboard (S3200SHV) built-in RAID controller and WD Velocyraptor 300GB 10000RPM (5 disks). The motherboard uses Intel Matrix and LSI. I tried both but no luck.



* Selecting "Finish" Sends me straight back to this same menu again.
* Selecting "Log in..." an then continue without entering any  iscsi-config makes a blue screen doing nothing. Ctrl C gets me out of  this screen and then present the same menu again.
* Selecting "Go Back"  sends me to the same blue screen, and so on...


Can you please point me to the track on how to pass this menu?


Thanks and more power!!!

---

### Post by c4rdinal on 2011-02-01
Hi Everyone,

I remember that it was not possible to install Linux with RAID 5 or 10. So I decided to add 1 more hard drive which will contain the /boot, /tmp and swap. I plan to allocate /, /var, /usr to my RAID 10 partition but during the section

!!Partition Disks 

SCSI5 (0,0,0) (sde) = 250 GB ATA
--here I can only find my non-RAID disk and RAID volumes cannot be seen. 


I selected Configure iSCSI volumes but there's no volume found.

Could someone help me please? Any thoughts about my problem?

---

