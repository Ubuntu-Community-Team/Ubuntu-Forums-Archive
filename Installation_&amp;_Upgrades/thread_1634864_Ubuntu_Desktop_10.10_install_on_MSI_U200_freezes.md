---
title: "Ubuntu Desktop 10.10 install on MSI U200 freezes"
date: 2010-12-01
forum: Installation &amp; Upgrades
---

### Post by guillend on 2010-12-01
Hi all,
I'm experiencing the same problem trying to install Ubuntu Desktop 10.10  into an MSI U200 Netbook. Same thing happens with Ubuntu Netbook 10.10.  

Initially I tried installing through the USB installer created via  System/Administrator/Startup Disk Creator. Burned the ISO image, booted  the netbook with it, then you see the colored dots for a while, and then  it freezes. 

Since it didn't work, I purchased an external DVD/CD drive to boot from  CD. And the same problem occurs. It freezes at the same place, with no  feedback of what's wrong.

So I downloaded Linux Mint 10, which was recently released, and seems to  be popular, burned the ISO into a CD, and tried it. It freezes too, but  it gives some feedback (I guess it is the same problem as Ubuntu  Desktop and Netbook): it says:

rt2800pci_mcu_status: Error - MCU request failed, no response from hardware.

I remember having other problems before with Ubuntu Netbook 10.04,  [related to wireless] but at least that one installed from USB. 

I'm going to try now with Ubuntu Mini Remix [[http://www.ubuntu-mini-remix.org/]]("http://www.ubuntu-mini-remix.org/%5D"), to see if I can pass the freezing point.

Cheers,

---

### Post by guillend on 2010-12-01
Hi all,

Tried with Ubuntu Mini Remix, and it freezes in the same place [trying  to install into MSI U200 via USB]. Fortunately, it gives some feedback too:

[30.337986] phy0 -> rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy, aborting.
[30.626739] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x00007010, value=0xffffffff

The problem seems to be the same as the previously reported ones. So the  same problem occurs with Ubuntu Netbook 10.10, Ubuntu Desktop 10.10,  Linux Mint 10, and Ubuntu Mini Remix 10.10.

Hope someone at Ubuntu is listening. 

Cheers,

---

### Post by guillend on 2010-12-01
I remember [from Ubuntu Netbook 10.04] the rt2800 problems with MSI U200 are related to the RaLink RT2800  Wireless Lan Linux Driver. I think the RT3090 driver was the appropriate one for MSI U200. 

[Just that I don't want to go back to install Ubuntu Netbook 10.04 and work my way back through all of those problems again; I hope someone can take this information into account when preparing the next Ubuntu Desktop and Netbook installations. ]

Will try the alternate installs ... [trying to avoid Windoze 7 as hell].

---

### Post by guillend on 2010-12-02
Hi all,

For the latest attempt I did the following:
- downloaded Ubuntu Desktop 10.10 **Alternate** i386 image;
- burned a CDR with it;
- installed it on the MSI U200 with external CD/DVD drive.

The installation went past the freezing point. If fact, it completed successfully.

Nevertheless, when I reboot to start the system, it freezes as soon as it switches from text mode into graphical mode. Now there is an error message, and it is similar to the ones I got before:

[21.031992] phy0 -> rt2800pc_mcu_status: Error - MCU request failed, no response from hardware
[21.844428] phy0 -> rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy, aborting.
[22.134158] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x00007010, value=0xffffffff

There must be a way of progressing past this point.

---

### Post by mörgæs on 2010-12-02
Have you tried running memtest from the installation CD?

---

### Post by guillend on 2010-12-03
Hi all,
Thank you Morgaes for your suggestion. Yes, the memtest passes complete, no errors.
 
I'll try the suggestions mentioned here:
[http://www.brighthub.com/computing/linux/articles/39504.aspx](http://www.brighthub.com/computing/linux/articles/39504.aspx)
 
Will post and update later.
Thanks.

---

### Post by weeblob on 2011-02-26
Hello, got u200 and had a problem with amd64 installation 10,04 and 10.10. I disabled PAVP(or howerver they call it  in BIOS.. in audio vid section) and installed 10.10 smoothly. Good luck.

---

