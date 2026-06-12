---
title: "Failed to start the X server : Installating Ubuntu 6.10 in Dell Inspiron 1525 Laptop"
date: 2008-08-08
forum: Installation &amp; Upgrades
---

### Post by syum on 2008-08-08
Hi,
I have recently received my new Dell Inspiron 1525 laptop with windows Vista already Installed. But I want my laptop to have a dual boot and I have been trying to install ubuntu 6.10. I have already made the necessary prerequisites in vista like shrinking the volume to have a free space that will be used for ubuntu installation. 
After that I booted from my ubuntu live cd and choosing the Start or Install Ubuntu, from the list of choices available, gives me the following error:
Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the x server output to diagonize the problem? After clicking the Yes option I have got the following important information:

....
(==) Using config file "/etc/X11/xorg.conf"
(WWW) I810: No matching device section for instance (BusID   OCI:0:2:1) 
(EE) No device detected
  Fatal Server Error
  No screens found
...............

I am stuck at this point.  I don't know what to do next. Is there anyone who come across or somehow has a solution to my problem? I really want to hear something from you.

Regards,

---

### Post by overdrank on 2008-08-08
> **syum said:**
> Hi,
I have recently received my new Dell Inspiron 1525 laptop with windows Vista already Installed. But I want my laptop to have a dual boot and I have been trying to install ubuntu 6.10. I have already made the necessary prerequisites in vista like shrinking the volume to have a free space that will be used for ubuntu installation. 
After that I booted from my ubuntu live cd and choosing the Start or Install Ubuntu, from the list of choices available, gives me the following error:
Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the x server output to diagonize the problem? After clicking the Yes option I have got the following important information:

....
(==) Using config file "/etc/X11/xorg.conf"
(WWW) I810: No matching device section for instance (BusID   OCI:0:2:1) 
(EE) No device detected
  Fatal Server Error
  No screens found
...............

I am stuck at this point.  I don't know what to do next. Is there anyone who come across or somehow has a solution to my problem? I really want to hear something from you.

Regards,

Hi and welcome. Firstly why are you using 6.10 edgy as it is not supported any longer. Can you down load the current version and try. Here are a couple of links that may help with the making of the cd
this link may help 
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto) 
Then you may want to do a checksum on the iso
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by ricardisimo on 2008-08-09
I'm on 7.04 getting the same error on boot. I get the Ubuntu progress bar, then that error. My problem is somehow connected to a new motherboard, a P4M900-M4, with only onboard graphics, no card, and only one RAM slot filled, with a 1Gig stick there.

The previous board had problems at boot as well (different ones) and wouldn't allow me to upgrade or install past 7.04.

---

