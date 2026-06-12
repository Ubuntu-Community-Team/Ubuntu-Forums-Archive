---
title: "Ubuntu boot problems"
date: 2008-10-01
forum: Installation &amp; Upgrades
---

### Post by XBrown on 2008-10-01
I have very little Linux experience, and have no idea whats going on.

I just installed a 320gb hdd, and installed ubuntu on the bigger drive.  I also have a 30gb drive.  The original 30gb drive is set as the master, and the new 320gb as the slave.  When I installed Ubuntu 7.1, it automatically set up partitions.  When I boot from the disc, it opens up to the tan screen, with the cursor.  At this point it hangs.  When I choose "Boot from first hard disk", I get"

Grub 1.5
Error 2

Before I turned off LBA on the larger drive, I would get "error 18".  Are my hard drives just too big?  Is there anything I can do?

---

### Post by modmadmike on 2008-10-01
I checked grub's web page and i got this :

# 2 : "Selected disk doesn't exist"
This error is returned if the device part of a device- or full filename refers to a disk or BIOS device that is not present or not recognized by the BIOS in the system.

Hope this helps

---

