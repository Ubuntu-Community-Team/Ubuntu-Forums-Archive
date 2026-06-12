---
title: "How do I install GRUB in the boot partition?"
date: 2006-08-16
forum: Installation &amp; Upgrades
---

### Post by s31248 on 2006-08-16
I want to install ubuntu on a second HD and install GRUB in the boot partition NOT the MBR of the primary HD.  How do I do this?  Other distributions allow you during install process to select the MBR or the first sector of the boot partition.  I don't see this option in ubuntu's install process...

Thanks for your help!

---

### Post by Klaidas on 2006-08-16
As far as I know, the LiveCD based install does not allow you to do that.
Alternate install CD might do the job
> Alternate install CD

The alternate install CD allows you to perform certain specialist installations of Ubuntu. It provides for the following situations:

    * creating pre-configured OEM systems;
    * setting up automated deployments;
    * upgrading from older installations without network access;
    * LVM and/or RAID partitioning;
    * **installing GRUB to a location other than the Master Boot Record;**
    * installs on systems with less than about 192MB of RAM. 


However, it does not have a GUI

---

### Post by s31248 on 2006-08-16
Thanks, that was easy!  I guess I should have scrolled down a little farther on the download page...

---

