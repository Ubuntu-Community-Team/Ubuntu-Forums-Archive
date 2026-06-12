---
title: "wireless broken after upgrade to 11.04 (Natty)"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by rziegler72 on 2011-04-30
After upgrading my laptop from 10.10 to 11.04 I can no longer connect to my home wi-fi.  It was working flawlessly for months before the upgrade.  The network manager just keeps spinning and nothing happens.

dmesg output just keeps showing this over & over again:


[ 1721.748149] ipw2200 0000:03:03.0: PCI INT A disabled
[ 1721.820199] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[ 1721.820204] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[ 1721.820319] ipw2200 0000:03:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 1721.820404] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[ 1721.955494] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[ 1730.452961] ipw2200 0000:03:03.0: PCI INT A disabled
[ 1730.523854] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[ 1730.523859] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[ 1730.523975] ipw2200 0000:03:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 1730.528062] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[ 1730.655407] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[ 2822.733715] ipw2200: Firmware error detected.  Restarting.
[ 2825.830079] ipw2200: Firmware error detected.  Restarting.
[ 2828.909032] ipw2200: Firmware error detected.  Restarting.
[ 2831.992010] ipw2200: Firmware error detected.  Restarting.
[ 2835.107507] ipw2200: Firmware error detected.  Restarting.
[ 2838.218445] ipw2200: Firmware error detected.  Restarting.


Any ideas what's going on here?  Let me know what other info I can provide.

Thanks in advance for any assistance you can provide.

---

### Post by Dale61 on 2011-04-30
If I had A$1.00 for every post about this, I would be very wealthy!

I'm in the same boat re: not being able to connect wirelessly.  I don't have a problem when connecting with an ethernet cable, but when it comes to wireless, all it does is just cycle until I manually kill the connection attempt.  With 10.10, I was able to connect with both at the same time as both connected automatically, but now, I get an auto connect via ethernet, but no sense whatsoever with wireless.

---

### Post by mjstealth on 2011-05-01
I got mine working by going to  On/Off button >> System Settings.

In there, I selected Hardware from the left column and clicked "Additonal Drivers" after that. 

Since I am using a Dell, I saw that I was running a Broadcom proprietary driver for my wireless. I basically deactivated it and restarted my computer.

And everything worked.

See if this works for you.

---

### Post by Dale61 on 2011-05-01
My wireless now seems to be working, on occasion, and has done so ever since I installed wicd.  I found this 'fix' by reading the ubuntuguide for Natty (try [http://ubuntuguide.org/wiki/Ubuntu:Natty]("http://ubuntuguide.org/wiki/Ubuntu:Natty"), but it is quite busy at the moment).

I had to get rid of network manager first, then apt-get wicd.  Once I put added the WAP security #, it found my wireless modem, as well as that of my SIL (in her room), and that of a neighbour.  It seems to connect OK, but it has to disconnect from the ethernet connection first.  Previously, I could connect to both, but hey, at least now I have wireless connectivity.

---

### Post by rziegler72 on 2011-05-04
Thanks for the responses.  Since I didn't have any solutions at the time, I re-installed Kubuntu 10.10 and all is fine.  The whole Unity/Gnome 3 thing scares me, which is why I thought KDE was a better fit for me...  I guess it remains to be seen if the same wi-fi issues would happen when upgrading to Kubuntu 11.04.  Would these solutions apply to KDE as well?

---

