---
title: "Installation stalls on USB detection (USB HID CORE)"
date: 2010-02-10
forum: Installation &amp; Upgrades
---

### Post by nhoffman on 2010-02-10
Hello, I used ubuntu on my previous system for a while, but switched to this system:
GA-K8N-SLi Mobo, AMD Athlon x2 64 4200, 2 GB ram,Windows 7.

I had no problem dual-booting and using my previous computer, but when I try to install the newest Ubuntu (64 bit version) from either a burned iso or wubi I get USB detection and initialization problems.  I get a cascade of errors like:

usb 1-8: unable to enumerate device
usb 1-8: device descriptor read/64, error -110
usb 1-8: not accepting address error -62

it seems like it goes through all eight usb channel trying to load and initialize, but returns an error for each one.  After this, it does appear to recognize my usb keyboard & mouse (it prints the name of the driver and seems to initialize ok), but when it gets to loading...

USB v2.6: USB HID Core

it hangs and does not recover.  Oddly it still responds to the keyboard, I see escape characters when I try a control sequence (like Ctrl-C), and if I Ctrl-Alt-Del it reboots with the appropriate message.  I have tried the boot parameters no apic, pic=noacpi, (I have heard of using irqpoll but I do not see that in the list of possible options) ... these do not help the situation.  I would be very grateful for any help, I've looked at other threads but they are all years old and don't shed very much light on my problem (besides some people having blacklist hid core, resulting in slow usb speeds, but I can't even get through installation).  Ubuntu is by far my favorite I tried Mandriva, which reads all my usb ok (but sucks, I couldn't stand it), Fedora which has been unstable for me, and Debian, which does not provide good installation options (either minimal package where you have to configure internet and install from command prompt or huge multi-DVD package).  I'm done trying the others and just want to get Ubuntu to work ... thanks.

By the way I forgot to mention, I also tried installing from a 8.04 DVD I had lying around that I got from a book a while ago, and I had the same problems.

---

