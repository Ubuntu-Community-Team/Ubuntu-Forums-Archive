---
title: "Karmic randomly freezing"
date: 2009-11-25
forum: Installation &amp; Upgrades
---

### Post by piccoloprincipe on 2009-11-25
While browsing (since is my typical activity), once or twice a day Karmic freezes and does not respond to mouse or keyboard, forcing me to reboot. The Wanda Fish applet in the panel also freezes, so it's not a keyboard or mouse problem.
What can I install/log/view/analyze to find out what is happening?

---

### Post by Grenage on 2009-11-25
Can you run a memtest? Ruling out bad RAM is normally the first step.

---

### Post by piccoloprincipe on 2009-11-25
Memory test did 3 passes with no errors detected. Freezing started with Karmic fresh installation, and it happened most while browsing and one time at the login (gdm) screen.

---

### Post by jaylsi on 2009-11-25
Do you have a nVidia graphic card? I had the same problem. I think the card goes bad, maybe not completely but it just does not do the work it supposed to. If you search Internet, many people have problem with nVidia working fine in XP but lockup in Vista. What I do is to remove it from motherboard and use on-board graphic for now and order a new card.

---

### Post by dhavalbbhatt on 2009-11-25
Do you have nVidia card? If so, what version of the drivers are you running?

---

### Post by piccoloprincipe on 2009-11-25
ATI, it's an old card and Compiz is not active:
```
[18:48:31][giorgio@Marty:~]$ lspci
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 11)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 11)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
**01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)**
01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (Secondary) (rev 01)
03:01.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
03:01.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
03:01.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 65)
03:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
03:05.0 Communication controller: Rockwell International HCF 56k Data/Fax/Voice/Spkp (w/Handset) Modem (rev 01)

```

---

### Post by dhavalbbhatt on 2009-11-25
I just did a quick search on google for the ATI card that you've mentioned. It seems that ATI does not provide drivers for Ubuntu anymore for the card that you're using. Having said that, I would imagine, the open source drivers were loaded at the time of Ubuntu installation. I am not the best person to help you with that - but I did find an old bug filed with Launchpad

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/291480](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/291480)

see if that can help you.

---

### Post by piccoloprincipe on 2009-11-25
Thanks for your support.
It seems that the graphic card is the cause since if I launch glxgears from the terminal the monitor goes off and the machine remains accessible by ssh and then freezes. I am researching how to change drivers if possible, otherwise I'll downgrade to 9.04 or even 8.04 which is a LTS.

---

### Post by piccoloprincipe on 2009-11-26
The open source drivers are used both in Jaunty (kernel 2.6.28, working) and Karmic (2.6.31, not working). I've found a ticket that addresses this regression.
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/486367](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/486367)

---

### Post by jaylsi on 2009-11-30
Before downgrading to previous working 9.04, try the 9.04 live CD first. In my case, the previously working version does not work any more after the freezing problem showed up. It could be that the card goes bad.

---

