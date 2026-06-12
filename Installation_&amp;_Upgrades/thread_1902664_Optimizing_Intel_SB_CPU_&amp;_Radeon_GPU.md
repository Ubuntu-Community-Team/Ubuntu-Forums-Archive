---
title: "Optimizing Intel SB CPU &amp; Radeon GPU"
date: 2011-12-31
forum: Installation &amp; Upgrades
---

### Post by outrageousgriot on 2011-12-31
Hello there everybody!  I would appreciate some advice if at all possible.  My current situation is as follows:

My new build has these specs:

-Gigabyte GA-Z68X-UD3H-B3 mobo w/ f10 bios
-Unlocked Intel Core i5 2500k processor
-XFX HD 6870 Dual Fan video card (w/ "eyefinity" or whatever it's called)
-16GB 1600 MHz Corsair Ram (The Black Vengeance 4 * 4gb pack)
-120GB Corsair Force 3 SSD

and I don't think the rest quite matters.  In any event, it was a great build and I got a lot of my parts at bargain prices at less than ~$800 for everything.

I have a few issues with optimizing my performance.  I installed 64 bit Ubuntu 11.04 the other day and I can't seem to get it running smoothly.  There are minor imperfections, and definitely would be real nice if they weren't there.  Read / write speeds are fast.  The OS seems to recognize my USB 3,0 ports that the mono has.  Ethernet was recognized OOB.

My problem is this GUI crap we all have learned to love.  I'm not big on it, but I do like the OS to look and feel nice.  I use the Ubuntu classic workspace, when doing things such as switching workspaces an minimizing windows (with no programs what so ever, just nautilus) it looks quite laggy and slow.  I've tried using the video drivers that Ubuntu suggests and some other drivers the I got from the AMD Radeon site.  Any help would be appreciated.  It's frustrating since I do a bit of programming in java and little animation crap that should run smoothly without a gpu lag out.
 
Please and thank you.

edit:  Looks like I got a bit too ahead of myself.  The ethernet/lan doesn't seem to work consistently.

Here is the lspci output:


00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation 2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 Display controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1c.4 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 5 (rev b5)
00:1c.5 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 6 (rev b5)
00:1c.6 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 7 (rev b5)
00:1c.7 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 8 (rev b5)
00:1d.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation 6 Series Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc Barts XT [ATI Radeon HD 6800 Series]
01:00.1 Audio device: ATI Technologies Inc Barts HDMI Audio [Radeon HD 6800 Series]
03:00.0 PCI bridge: Integrated Technology Express, Inc. Device 8892 (rev 30)
04:02.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)
05:00.0 USB Controller: Device 1b6f:7023 (rev 01)
06:00.0 USB Controller: Device 1b6f:7023 (rev 01)
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
08:00.0 IDE interface: Marvell Technology Group Ltd. Device 917a (rev 11)

solved: 
purge removed proprietary driver, installed open source drivers, reboot, back to perfection ;)

---

### Post by 2F4U on 2011-12-31
Thats interesting. I am running Unity (I guess you are talking about Unity, right?) on a rather crappy ATI Radeon 4550 passively cooled graphics card and open source drivers without any problem. Everything is smooth, no lags or artefacts. Your graphics card tops mine by far, so you should do far better. 
Are sure that the graphics card is the problem, or is something else running in the background. It may even be due to some strange sort of hardware incompatibility.

---

### Post by outrageousgriot on 2011-12-31
> **2F4U said:**
> Thats interesting. I am running Unity (I guess you are talking about Unity, right?) on a rather crappy ATI Radeon 4550 passively cooled graphics card and open source drivers without any problem. Everything is smooth, no lags or artefacts. Your graphics card tops mine by far, so you should do far better. 
Are sure that the graphics card is the problem, or is something else running in the background. It may even be due to some strange sort of hardware incompatibility.

It doesn't matter if I use the classic gnome or the newer unity looking desktop - it's all the same.  Maybe you can suggest me some open source drivers?  That may be it, because I am using the proprietary driver.

My wired internet also works inconsistently.  Hmm...

edit: edited my first post for my lspci info

edit again:  Good news!  I've managed to purge the propietary driver and install the open source driver and everything is working nice and smoothly now!  Gotta love open source ;)

Can't believe I didn't go with the open source driver in the first place xD

---

### Post by outrageousgriot on 2012-01-18
I just wanted to post back with more.  Apparently the sync to vbank option in the OpenGL area in the compiz settings slows things down tremoundously.  By disabling it the performance of my my HD 6870 is incredible now with both open source drivers and proprietary drivers.

I'm curious to hear if anyone knows how to toggle this sync to vbank option and other similar options available via the compiz GUI via terminal.

---

