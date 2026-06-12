---
title: "Wireless in Karmic, HELP!!!"
date: 2009-11-28
forum: Installation &amp; Upgrades
---

### Post by papajonesy on 2009-11-28
Hello, since upgrading from 9.04 I can't see my wireless network in the tray. It can find a few of my neighbors networks, but it can't seem to find any wireless N networks like mine. I am using rt2870 chipset. Thanks

---

### Post by edkwok on 2009-11-28
Make sure you are talking on the same channel, it should auto detect, but never knows.  if you see your neighbors maybe you are not talking on the right channel.  You can check this be login to your Access point and go through each channel see if you get one right.....

//ed

---

### Post by vxice on 2009-11-28
when I installed linux on my laptop it had no wireless network viewer available.  It could see all the networks using command line commands but I had to install a gui wireless manager.  I went with wicd but any will do, you might need to uninstall the default wireless manager or add its complimentary gui.

---

### Post by mizunoX on 2009-11-30
> **papajonesy said:**
> Hello, since upgrading from 9.04 I can't see my wireless network in the tray. It can find a few of my neighbors networks, but it can't seem to find any wireless N networks like mine. I am using rt2870 chipset. Thanks

It could be that your network is broadcast at 5Ghz.

This driver in Karmic (or the new kernel?) seems to be missing some important features such as 5Ghz support.
My network SSID disappears from the list if I switch to 5Ghz as well.  Didn't happen with Jaunty.

---

