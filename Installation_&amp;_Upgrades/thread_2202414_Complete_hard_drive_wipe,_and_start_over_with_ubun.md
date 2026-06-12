---
title: "Complete hard drive wipe, and start over with ubuntu install"
date: 2014-01-29
forum: Installation &amp; Upgrades
---

### Post by cdahl7 on 2014-01-29
I messed up install with nvidia driver bs and have had zero luck fixing the issue in other threads. Now when I try to "completely wipe and start over" from ubuntu live installer it doesn't work and I'm stuck with a f&*$ed up system. I need instructions to completely wipe hard drive to start over. This includes wiping boot data, because i think part of the problem is my boot loader is messed up. 

To be clear, I don't need to fix anything, I have no data that I need to save. I have previously posted regarding trying to fix boot loader, but if someone has an easy way to completely wipe and completely start over, that would be best at this point.

THANK YOU
Regards,
-CD

---

### Post by sudodus on 2014-01-29
Do all these operations when booted from another drive, for example your Ubuntu install CD/DVD/USB drive.

I suggest that you ***wipe the first megabyte*** (overwrite with zeros). After that you can start all over again with ***gparted***, first select Device and create a partition table, then create partitions, and after that install Ubuntu.

You can wipe with ***dd***, but it is risky, if there are other drives, that you don't want to overwrite.

---

### Post by fantab on 2014-01-29
Or...

USE Gparted from Ubuntu Live USB/DVD.
Open Gparted... Select your HDD. In the Menu click on 'Devices' -> 'create new partition table'. Default partition table is 'msdos'. If you have UEFI then go to 'Advanced' and select GPT.
When a new partition table is created all previously existing partitions and data will be erased.
Then go on to make new partitions and install Ubuntu afresh.

---

### Post by Marc_Morici on 2014-01-29
Try this, burn the iso to CD and boot from CD.  You can either quick format or full format using this.

[https://www.dropbox.com/s/sa4da9aabu7bfdi/gwscan.iso](https://www.dropbox.com/s/sa4da9aabu7bfdi/gwscan.iso)

---

