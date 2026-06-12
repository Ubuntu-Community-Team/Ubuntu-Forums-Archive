---
title: "Ubuntu Video Driver"
date: 2014-07-18
forum: Installation &amp; Upgrades
---

### Post by WillEllen on 2014-07-18
How can the video driver be copied from an older version of Ubuntu and installed in the latest  version.  (There is a compatibility issue with the new driver and some display cards.)

bill

---

### Post by Mark Phelps on 2014-07-18
If it's a proprietary driver, that won't work because those are kernel version dependent and a newer Ubuntu would have a different Linux kernel version.

There is also the issue of compatibility between the video driver and the X-server version, and if that is a problem, the old driver is also not going to work in the newer Ubuntu.

Would be better if you first told us what video card you have and whether it's the proprietary driver or open-source driver you want to copy.

If you don't know the video card, open a terminal, enter "lspci" and look for the line containing "VGA" -- and post that info back here.

---

### Post by WillEllen on 2014-07-21
This computer has built-in (on MB) video.  I had resolved the same problem on another computer just by changing tle video card.  On this one SUSE 14.04 with LXDE GUI works well but I do not want to give up on Ubuntu. The following is the output info. from "lspci"

guest@kg-cmanager4:~> /sbin/lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
01:09.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
guest@kg-cmanager4:~> 

Thanks, Bill

---

### Post by Rob Sayer on 2014-07-21
According to this:

[http://askubuntu.com/questions/185079/which-version-of-ubuntu-will-work-out-of-the-box-on-intel-82845g-board](http://askubuntu.com/questions/185079/which-version-of-ubuntu-will-work-out-of-the-box-on-intel-82845g-board)

that card is quite old and not even supported by intel anymore.

I suspect the reason you could get SUSE with LXDE to work OK is because it's the LXDE desktop more than anything else.  You are not going to be able to use openGL with that card AFAICT.

Try Lubuntu.

---

### Post by Mark Phelps on 2014-07-21
> 00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)

That's back to the pre-Vista, Windows XP days for intel video chipsets. Not surprised it won't work with Ubuntu.

Lubuntu, as Rob Sayer recommended, is most likely to work, and if that does, you could then try Xubuntu -- but that's less likely to work.

---

### Post by WillEllen on 2014-07-23
The latest version of Xubuntu has the video driver compatibility issue, the previous LTS version is good until an update.
Bill

---

