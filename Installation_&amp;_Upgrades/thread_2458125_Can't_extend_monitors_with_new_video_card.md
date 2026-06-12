---
title: "Can't extend monitors with new video card"
date: 2021-02-16
forum: Installation &amp; Upgrades
---

### Post by peyre on 2021-02-16
I use two 17" analog monitors with my desktop computer.  I had them plugged into an older NVidia card (one using a VGA-DVI adapter), but the card seems to have died.  I bought a replacement card, a VisionTek Radeon HD 5450 2GB DDR3.  Now I get picture on both monitors, but it's mirrored.  When I uncheck Mirror displays in Display, it seems to be trying for about 10 seconds (it seems to be showing on both monitors what should be just on the secondary), then it comes back to the mirrored displays.  Additional Drivers says there are no drivers available.  lspci returns:
```
00:00.0 Host bridge: Intel Corporation 4th Gen Core Processor DRAM Controller (rev 06)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)
00:02.0 Display controller: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller (rev 06)
00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 05)
00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d5)
00:1c.3 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #4 (rev d5)
00:1c.4 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #5 (rev d5)
00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation H81 Express LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 05)
00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Cedar [Radeon HD 5000/6000/7350/8350 Series]
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Cedar HDMI Audio [Radeon HD 5400/6300/7300 Series]
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0c)
04:00.0 Network controller: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter (rev 01)

```

I've looked in the BIOS and there's no option for onboard vs. discrete video card.  There is an option to enable/disable Intel multi-monitor capability, but turning it off or on doesn't affect this (no surprise there, but was worth checking).  This is a Dell Inspiron 3847 from 2016.

---

### Post by peyre on 2021-02-19
I know no one's paying attention to this post, but tonight I dug out my old desktop PC from 2009, which the video card had run in before.  I plugged the old video card in (plus my boot disk), and this time I got one screen, which I hadn't before, but still, the whole point is to have two.  I shut down and put in the new video card and it mirrored the displays on this computer, too.  Tried the new and old video cards on the newer computer again, still the same result (except this time I think I managed to get one display working with the old video card, but never two).  So frustrating!  This really shouldn't be so difficult.

---

### Post by peyre on 2021-02-20
Strange!  With a lot of trial and error, plugging/unplugging and booting up again, booting with a live disk, etc., I seem to have found something that worked.  I'm using a very old PCI-E card so it's probably not very capable, but it extends the Desktop, which is what I really wanted. 

The only thing now is that in all that trial and error I did, somewhere along the way I disappeared all my Desktop icons.  They're still there - there are 53 items in ~/Desktop - but they don't show *on the Desktop*.  Anyone know how to restore them?

Also, oddly, right-clicking doesn't do anything on the Desktop.  I imagine that's probably related somehow.

---

### Post by peyre on 2021-02-21
Huh, that didn't resolve the issue.  What ended up fixing it was upgrading to 20.10 (form 20.04 LTS).  Looks like it was a software issue with my OS or desktop environment.  I still don't have my icons though.

---

