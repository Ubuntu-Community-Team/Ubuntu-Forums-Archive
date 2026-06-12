---
title: "Wired Minimal Install - No Network Interfaces Detected"
date: 2010-07-18
forum: Installation &amp; Upgrades
---

### Post by BLaZuRE on 2010-07-18
I'm trying to do a minimal install via a USB flash drive. Everything was good until it tried to recognize my network (wired). It showed "No Network Interfaces Detected" (On Ubuntu and Debian).

I wish to do a minimal install since I want to install the programs I want myself. Plus, I have a small flash drive.

I'm using an Atheros AR8151 PCI-E as my card (as shown by Windows). I also have a wireless, though I don't care much about that, wired will probably be easier.

Through the command shell, I can see Ethernet Controller: Atheros Communications AR8151 v1.0 Gigabit Ethernet (rev c0).

So ... it's being recognized but not detected?

When I do plug the Ethernet cable in, I don't get the lights on during Linux installation but they do come on in Windows.

Any ideas? If I need some additional driver, can I somehow add it to the minimal installation?

So, I was looking through the log file and found that i82365 could not be loaded, a PCMCIA controller. I'm assuming this is separate from the NIC and interfaces between the bus and the NIC.

Anyway, no idea whether it's because it couldn't find the drivers or because the controller was incorrectly identified. But I'm pretty sure this is why I can't get my network card to work.

---

### Post by davidmohammed on 2010-07-18
... see this [thread]("http://ubuntuforums.org/showthread.php?t=1476231") - looks like your ethernet is not supported in the current kernel but you can get it to work by compiling the source code.

---

### Post by BLaZuRE on 2010-07-25
I don't know how'd I'd get it from source.  It's not included on the minimal install and when I do the full install via Live USB, it freezes once at the desktop.

---

### Post by BLaZuRE on 2010-07-25
It also freezes at the login user selection screen once installed.  With the live USB, I'd at least have a responsive keyboard + mouse until the taskbar/menu bar appeared (with the desktop background + icons loaded).
The shell works properly from recovery mode via Grub.  I've looked through the logs, though found nothing that would alert me why Ubuntu is hanging.

Any ideas?

_**Edit:**_ Freezing resolution:

When at GRUB load menu, press 'e' for edit
Delete 'quiet and splash'
Replace with 'nomodeset'

Works *yay* ... and it only took 3 months to casually stumble on an article that said that.

---

