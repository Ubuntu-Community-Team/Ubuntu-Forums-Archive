---
title: "Freeze installing  10.10 on MSI U200 Netbook"
date: 2010-12-01
forum: Installation &amp; Upgrades
---

### Post by guillend on 2010-12-01
Hi all,
I'm experiencing the [same problem]("http://ubuntuforums.org/showthread.php?t=1634057") trying to install Ubuntu Desktop 10.10 into an MSI U200 Netbook. Same thing happens with Ubuntu Netbook 10.10. 

Initially I tried installing through the USB installer created via System/Administrator/Startup Disk Creator. Burned the ISO image, booted the netbook with it, then you see the colored dots for a while, and then it freezes. 

Since it didn't work, I purchased an external DVD/CD drive to boot from CD. And the same problem occurs. It freezes at the same place, with no feedback of what's wrong.

So I downloaded Linux Mint 10, which was recently released, and seems to be popular, burned the ISO into a CD, and tried it. It freezes too, but it gives some feedback (I guess it is the same problem as Ubuntu Desktop and Netbook): it says:

rt2800pci_mcu_status: Error - MCU request failed, no response from hardware.

I remember having other problems before with Ubuntu Netbook 10.04, [related to wireless] but at least that one installed from USB. 

I'm going to try now with Ubuntu Mini Remix [[http://www.ubuntu-mini-remix.org/]](http://www.ubuntu-mini-remix.org/]), to see if I can pass the freezing point.

Cheers,

---

### Post by guillend on 2010-12-01
Hi all,

Tried with Ubuntu Mini Remix, and it freezes in the same place [trying to install into MSI U200 via USB]. Fortunately, it gives some feedback:

[30.337986] phy0 -> rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy, aborting.
[30.626739] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x00007010, value=0xffffffff

The problem seems to be the same as the previously reported ones. So the same problem occurs with Ubuntu Netbook 10.10, Ubuntu Desktop 10.10, Linux Mint 10, and Ubuntu Mini Remix 10.10.

Hope someone at Ubuntu is listening. 

Cheers,

---

