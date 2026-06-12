---
title: "Operating system not found"
date: 2012-01-24
forum: Installation &amp; Upgrades
---

### Post by charlie321 on 2012-01-24
My system:
- Lenovo X121e laptop
- Crucial M4 128gb 7" SSD
- Ubuntu 11.10
- USB wireless keyboard & mouse (going into a single USB wireless receiver - a Microsoft Wireless Optical Desktop Receiver 3.0)

Minor problem but tedious nonetheless.  My laptop ran out of battery and auto shut down whilst the USB wireless keyboard/mouse was connected.  If one then disconnects the USB cable whilst it is off then restarts the laptop, then the computer doesn't seem to detect the OS once restarted! I get a "No operating system" message.

It is all fine if I switch it off, replug the USB wireless keyboard/mouse and restart (then unplug the USB when it is running).  But is there a fix for this so I don't have to worry in future if the thing shuts down with something connected?  In this case it was a USB wireless mouse/keyboard but it is easy to forsee it happening with other things (printers/memory sticks etc).

Cheers

C.

---

### Post by darkod on 2012-01-24
This is very strange, the no OS message shouldn't relate to having a wireless combo connected or not. And I have no idea why are you worried so much about shutting down in future while "things" are connected. This is more a glitch than a rule.

Have you tried setting the boot flag on any partition, usually your root partition? If you have only ubuntu it doesn't set up the boot flag because linux doesn't use it like windows, but some boards don't boot if they can't see a boot flag present, regardless if it's not needed.

But that would apply with or without the wireless combo connected. Apart from this, I can't see a reason between a no OS message and a wireless combo.

---

### Post by charlie321 on 2012-01-25
Yep, just an ubuntu partition.

Absolutely correct - it is only a glitch. All I'd need to do if I come across it again is plug in whatever USB device(s) which was plugged in on shutdown and it should restart fine. 

The only possible disaster I can see happening is the thing auto shutting down with something connected and me grabbing it and rushing off abroad without whatever was plugged in, only to discover the "No OS found." message...

---

### Post by mastablasta on 2012-01-25
it could be that the mouse mounts wrong (as a disk device or something ). is the boot order set mabye to boot form USB? though if it's not there it should skip it. hmm strange...

---

