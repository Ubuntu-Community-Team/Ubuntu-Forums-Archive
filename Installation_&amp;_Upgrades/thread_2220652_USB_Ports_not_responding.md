---
title: "USB Ports not responding"
date: 2014-04-28
forum: Installation &amp; Upgrades
---

### Post by darkside1008 on 2014-04-28
So here is the issue on both my secondary computer and my work server that I am installing ubuntu 14.04, this happens on both Server and Desktop edition on both computers.   I put the CD's in and go to the install screen and when it gets to the screen to move your keys by using keyboard or mouse it does not move.  However the Server has a PS2 port for it's mouse and that works but the usb keyboard does not respond it doesn't even get power so I can't even light up the caps lock key or anything.  I am not sure what I have to do to get the USB ports working because no matter what port I plug it into it does not respond.

I hope someone can give some insight because I've been at this a couple of days and I'm at a loss.

Thank you

---

### Post by Awks_Panda on 2014-04-30
This problem also occurred on my machine for both keyboard and mouse.

To add to this post, I get the errors below at kernel boot up time which gets spammed across the screen and alternates between status -71 and -32. I have a Razer BlackWidow 2013 and Razer DeathAdder.

> kern.log.1:Apr 27 22:53:53 ninja-coder kernel: [  108.596750] hid-generic 0003:1532:0037.0009: can't reset device, 0000:00:1d.0-1.6/input2, status -71
kern.log.1:Apr 27 22:53:53 ninja-coder kernel: [  108.850640] hid-generic 0003:1532:0037.0007: can't reset device, 0000:00:1d.0-1.6/input0, status -32



I have tried to update the kernel to v3.15 RC2 however, the error occurred on that too so I am back to v3.13 that was released with Trusty 14.04.

I did manage to temporarily fix this problem by plugging in both devices to USB 3.0 ports instead of USB 2.0 however, I imagine this is not a suitable fix for everyone.

---

