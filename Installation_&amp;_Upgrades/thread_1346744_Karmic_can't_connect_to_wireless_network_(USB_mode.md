---
title: "Karmic can't connect to wireless network (USB modem)."
date: 2009-12-05
forum: Installation &amp; Upgrades
---

### Post by SuperEngineer on 2009-12-05
Anyone got an idea as to how to get USB wireless modem to connect to the network (recognised & declared in wireless network list) that Jaunty has no problem with????

---

### Post by darkod on 2009-12-05
You mean usb wi-fi adapter or actually a modem? Modems are usually connected to your phone line or similar.
Anyway, better place for this thread is in Networking & Wireless section, there are more people there who know about it.
One advice I can give you is check your usb devices with:
sudo lsusb

That will list them all including your modem/adapter and its chip model. Then you can google for solutions according to the chip model which has nothing to do with the modem manufacturer usually.

---

### Post by SuperEngineer on 2009-12-05
Thanks  Darkod.  Will do.

---

### Post by SuperEngineer on 2009-12-28
[SOLVED]

                 Workaround discussed in [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/460323](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/460323) has provided a fix for now but ... this issue is still a bug for correction prior to next release to maintain Ubuntu's good reputation.
 workaround details...
 Fixed with:
 Step1: add "blacklist rt2800usb" to:
           /etc/modprobe.d/blacklist.conf
Step2: add "rt2870sta" to:
           /etc/modules
Step3: Reboot.
 Connectivity now working as per Jaunty.

---

