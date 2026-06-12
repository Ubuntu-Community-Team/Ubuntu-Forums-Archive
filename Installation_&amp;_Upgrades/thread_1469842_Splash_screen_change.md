---
title: "Splash screen change?"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by toxic9813 on 2010-05-02
When I upgraded my Ubuntu 9.10 to 10.04 LTS (beta, then RC, then final,) that I've had for a while, the splash screen is displayed in 640x480 and flickers. My friends Ubuntu Machine that I set up for him, almost the same specs, on the same monitor, but a raw install of 10.04, his splash screen is at full resolution, (1280x1024) with that cool pulsating glow. Is the upgrade different?

---

### Post by toxic9813 on 2010-05-02
bump. going to the bottom really quick.

---

### Post by toxic9813 on 2010-05-02
Bump again? Delete this thred.

---

### Post by davidmohammed on 2010-05-02
the mods dont like people bumping their own thread twice in less than a day...

what's the specs of your laptop - can you do a lspci and post that here.  Sounds like you have a graphics issue.

---

### Post by toxic9813 on 2010-05-03
Sorry about that...

I made a thread on general discussion. It has more traffic; but I need all the help I can get. (Not using a laptop)

Here's my lspci:

lstoxic@toxic-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82946GZ/PL/GL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82946GZ/PL/GL PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7300 GS] (rev a1)
04:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5786 Gigabit Ethernet PCI Express (rev 02)

---

### Post by toxic9813 on 2010-05-03
I found this and tried it. Rebooting.

[http://www.webupd8.org/2010/03/how-to-get-plymouth-working-with-nvidia.html#comment-41037671](http://www.webupd8.org/2010/03/how-to-get-plymouth-working-with-nvidia.html#comment-41037671)

---

### Post by toxic9813 on 2010-05-03
Broke Ubuntu. I have live CD's to reinstall.

:cry:

---

