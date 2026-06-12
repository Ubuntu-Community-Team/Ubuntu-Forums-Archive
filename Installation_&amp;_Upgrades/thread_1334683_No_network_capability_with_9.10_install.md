---
title: "No network capability with 9.10 install"
date: 2009-11-22
forum: Installation &amp; Upgrades
---

### Post by Albert Seminatore on 2009-11-22
I have a Toshiba P505.  I have been running Ubuntu 9.04 with no problems.  It installed with a working wirless network.
I have installed Ubuntu 9.10 from a down loaded iso disk and from an online upgrade.  The results are the same.
  There is NO Ethernet or WIRELESS.  I do have the little icon but no bars.

The  iwconfig gives:    lo  now wireless extensions.
The  lspci -v gives:
      Network controller.  Intel Corp. Wireless WiFi Link 5100
      SubSystem:  Intell Corp. Device 1201
      FLags:  bus master, fast devsel, latency 0,  IRQ 17 ( for U9.10)
                                                   IRQ 2297 ( for U9.04)
      Kernal driver and modules are both  iwlagn
The ifconfig gives:  only the Loopback Nothing else for U9.10
                     in U9.04 it reports values for eth0; lo; wlan0

How do I get Ubuntu 9.10 to recognize my wireless connection?

---

### Post by HeadHunter00 on 2009-11-22
Sorry mate, I am guessing that the problem is only in your laptop. I have the exact same laptop with the exact same specs, but I didn't have any problems like you.

---

### Post by HeadHunter00 on 2009-11-22
I think there isn't any wireless networks around you.

---

### Post by Albert Seminatore on 2009-11-23
I do have a wireless network!  I can see the router from where I sit.
Under Windows Vista every thing works FINE.
Under Ubuntu 9.04 everything works FINE.

Under Ubuntu 9.10 there is NO Network connection.  Ethernet doesn't work and the wireless doesn't work.  The BIOS says ethernet is enabled.

Thanks for your reply......  Al

---

