---
title: "Will ATI r350 cards work?"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by ThomThom on 2008-10-30
The release notes says this:

> ATI "fglrx" video support

The ATI video driver in 8.10 drops support for video cards with r300 based chips (the Radeon 9500 - X600 Series of cards). If you have such a card, please use "Hardware Drivers" at System/Administration to disable it before the upgrade. Please see bug 284408 for more information 

I got an ATI Radeon 9800 card. 

From $ lspci -v I get this:

```
01:00.1 Display controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro] (Secondary)
	Subsystem: ATI Technologies Inc Unknown device 3003
	Flags: bus master, stepping, 66MHz, medium devsel, latency 64
	Memory at e8000000 (32-bit, prefetchable) [size=128M]
	Memory at fe9f0000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: [50] Power Management version 2
```

Would a R350 card be "R300 based"? Or am I safe? Can I upgrade without disabling the driver? Will I still get hardware acceleration?

---

### Post by peakshysteria on 2008-10-30
You are undeniable within the Radeon 9500 - X600 range since your card identifies as **Radeon 9800 Pro**. I myself am a bit reluctant to upgrade since I'm still not sure my X700 Pro card is supported. Our best bet (if something bad happens after an upgrade) should be [Method 2: Manual Install Method]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Install_Method") of the installation guide. This worked smooth for me after my last install. I haven't found any encouraging intel on Intrepid Ibex and ATI yet (this still don't mean that something bad will happen). As of know I think I will wait and see how the ATI people responds...

---

### Post by ThomThom on 2008-10-30
I'm considering waiting it out. The last two times I've updated Ubuntu I've had to mess about for hours to get the hardware acceleration working. I got a system that works now, with hardware acceleration. Not getting hardware acceleration would feel like taking a step back... :(

What does R300 and R350 mean?

---

### Post by peakshysteria on 2008-10-30
I'm not an expert I must admit. Just amazed right now that my 8.0.4.1 is smoother than ever with the ATI 8.9 version of their driver. So as I mentioned above I'm still a bit reluctant to jumping on Intrepid until someone can verify which ATI card is supported and which is not.

Anyway man, take a look at [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) and [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by ThomThom on 2008-10-30
I'm amazed how quickly Google indexes this forum. I was doing some more searching after I initially posted this question and I already find my post at the top of the search list for "Ubuntu 8.10 ati r350" ...

---

### Post by ThomThom on 2008-12-21
Has there been any change to the support of these cards?

I was looking at the bug report which the upgrade page referred to: [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/284408](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/284408)

Do I understand it right that there's been released a new ATI driver which brings back support for these cards on 8.10? If so, would I then upgrade Ubuntu by first disabling the existing drivers, perform the Ubutnu update, then install the new ATI drivers?

---

### Post by ThomThom on 2008-12-26
bump?

---

