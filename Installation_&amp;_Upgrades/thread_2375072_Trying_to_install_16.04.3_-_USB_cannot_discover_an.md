---
title: "Trying to install 16.04.3 - USB cannot discover any wireless networks."
date: 2017-10-21
forum: Installation &amp; Upgrades
---

### Post by Bobby_James on 2017-10-21
I am trying to install 16.04.3 on a Windows 10 HP machine. I have downloaded the iso and copied it to a USB using Rufus as recommended. My goal is a dual boot machine. 

  However, when I boot from the USB, it cannot detect any wireless networks. The same applies when I select "try Ubuntu" from the boot menu. Networking and wireless are enabled but no wireless networks are shown. 

 I have no idea what could be wrong. Can anyone please help?

---

### Post by TBerk on 2017-10-22
Most likely your plain vanilla  'LiveCD' doesn't have any drivers loaded to enable the WIFI Chipset.  (I've been through this a lot with having different computers that relied on Broadcom Drivers).

Someone else might have a more complete solution right on the tip of their fingers but I'm going to suggest you look into finding out what wifi sub-set the hardware is using and try to install via an Ethernet Cable (hard-line) if only at first; then you might find joy w/ the 'Additional Drivers' option in the Control Panel.

---

