---
title: "Ubuntu Remix Freezes at Startup (Netbook)"
date: 2010-02-21
forum: Installation &amp; Upgrades
---

### Post by hyperhelium on 2010-02-21
I'm posting this hoping it might help someone.

When I was trying to install Ubuntu 9.10 remix in a HP mini netbook, I had some issues I had to fix:

1. usb-creator didn't work. When I tried to make de usb-startup disk the panel didn't recognize the empty space in the usb and the "create" button was not highlighted, so I couldn't move forward.

Solution: I reinstalled the package at synaptic-manager (and its fellow components), and then everything went fine when doing the bootable usb.

2. Once I managed to boot from the usb, I installed ubuntu as usually, but then 
problems hit again. The computer froze when starting up. (actually I had some trouble when installing straight from the usb's first option "install ubuntu", so I had to run the try ubuntu option and run install from there).

So, once I managed to have it installed in the hard disk, I booted and it froze. It wouldn't even let me see the ubuntu logo.

Solution: Fortunately I had left a small partition with windows, in case I wanted to sell the computer or something, so I started up with windows and reinstalled the newest boot file version from HP's page. That kinda did the trick. I rebooted, now using ubuntu's system, and I managed to enter to the desktop.

IF YOU'RE PLANNING TO GET COMPLETELY RID OF WINDOWS, IT MIGHT BE A VERY GOOD IDEA TO INSTALL THE NEWEST BOOT FILE FOR YOUR NETBOOK FIRST

3. After I had been able to log in to the desktop and so, I rebooted again to verify everything was OK. And the computer froze again! I noticed something funny though. When I booted with a USB memory stick plugged in, the system would launch. If there was no USB memory stick, it would froze again.

So, I thought the problem had something to do with the order of the bootable devices. Remember you had to change this order when starting from your new USB-bootable image.

Solution, I booted again, with the stick on, and then changed the order of the devices to the original, this meaning putting the hard drive as the first boot device in the bios configuration.

4. After doing so, I still had some issues with booting, so once I managed to log in to the desktop, I immediately plugged the internet cord (wifi wouldn't work yet since I didn't have the broadcomm driver installed yet) and made a system update.

It seemed to do the trick.

5. I rebooted and it worked fine, I installed the hardware drivers and the rest of the install process went smoothly.

I'm sorry I wrote this the way it is. I'm not an experienced programmer or computer expert, I'm just stubborn, but I thought this might help somebody.

Fortunately I managed to have Ubuntu Karmic Remix running in my Netbook. :)

---

