---
title: "Installed, but odd USB errors on boot"
date: 2006-02-20
forum: Installation &amp; Upgrades
---

### Post by LordBug on 2006-02-20
I finally converted my main PC from WinXP to Ubuntu.  Everything went as expected (read - few problems), and it's all up and running (I'm posting from it).

However, I have an odd issue with USB.  It works... mostly.  I can see all of my USB devices, and they work.  The issue is what happens during boot.

Grub goes ok, the initial boot starts, and Ubuntu switches to the framebuffer screen.  I see "Loading Modules" and the system hangs for a minute or so.  It flips back to 80x25 text mode and sits there for another moment.  I then get a message (I had to write fast, so I hope I got it all):

drivers/usb/input/hid-core.c: usb_submit_urb (ctrl) failed.

The system then boots up normally.  Google'ing the message, it seems to be some kind of USB query going on and crapping out.  I just have no idea which device, exactly, is doing it.  Is there an easy way, short of testing USB devices one at a time, to figure out what's causing this?

Also, XSane and IScan each take 1-3 minutes to actually load up.  They do, eventually, load and the scanner (Epson 3170) works fine.  I'm not sure if this is related to the other USB issue.  I had this same scanner hooked to my second Linux box, and XSane and IScan both fired up in seconds.  Any thoughts on this are appreciated to.

---

### Post by jml75 on 2006-02-20
Hi,

What processor, chipset do you have in your computer?

---

### Post by LordBug on 2006-02-20
Oops, guess that information would help, huh?

Athlon 64 3500 (using x86 install)
nForce 4 chipset

---

### Post by LordBug on 2006-02-22
Update:

I pulled the system completely apart so I could add a sound card (the onboard couldn't do hardware mixing).  After I re-built it, the boot up still hung at "Loading Modules...", flipped to the 80x25 boot screen, but the USB message was gone.  I know I moved a few of my USB connections to other ports, so now I'm wondering if it's a port issue.

---

### Post by LordBug on 2006-02-23
Issue solved.  I had to resort to pulling 1 USB at a time and re-booting, but it appears to have been my UPS doing it.  It uses a USB to Serial adapter (shipped with the UPS).  Guess I'll just have to move it to my serial port instead.

---

