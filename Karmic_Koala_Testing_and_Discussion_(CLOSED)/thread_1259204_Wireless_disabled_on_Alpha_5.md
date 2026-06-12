---
title: "Wireless disabled on Alpha 5"
date: 2009-09-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Stoneface on 2009-09-06
I have just installed Karmic Koala and despite Synaptic Manager, Pulse Audio and a few other programs crashing on me it is working. When I try to send crash report I could not somehow. But About that I talk later.
My issue now is that my Wifi connection is *disabled*. Not in Bios as I am using the same wireless Atheros driver after rebooting into Windows. Furthermore I have no network manager option in the menu nor do I have a menu icon with all the networks available. I tried an Ethernet connection elsewhere and that works.
How can I enable wifi again and how can I get more network management control?

---

### Post by Stoneface on 2009-09-13
Well, no help here. I just reinstalled Jaunty for now and will work on KK on a Virtual Box.

---

### Post by philinux on 2009-09-13
Did you report the bug to launchpad. After all thats what the alphas are for, shaking out the bugs. Not all hardware is created equal.:P

---

### Post by darkstaar on 2009-09-13
> **Stoneface said:**
> My issue now is that my Wifi connection is *disabled*.

How can I enable wifi again and how can I get more network management control?

This may be a silly question but...did you check to see if you could enable a restricted driver? I had to do this under Alpha 4 for my Broadcom hardware. This driver installed and ran automatically under Jaunty. This wasn't the case with Karmic. I actually had to select it upon install.

-- Leisa

---

### Post by taavikko on 2009-09-13
Without giving proper details, it's freaking hard to tell where the problem might be.

ath9k is a mess: [https://bugs.launchpad.net/bugs/414560](https://bugs.launchpad.net/bugs/414560)

Also somehow the devices can be blocked, so check with
```
rfkill list
```

---

### Post by philinux on 2009-09-13
> **Stoneface said:**
> Well, no help here. I just reinstalled Jaunty for now and will work on KK on a Virtual Box.

Try this.
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

---

