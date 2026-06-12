---
title: "really weird usb problem"
date: 2008-01-01
forum: Installation &amp; Upgrades
---

### Post by baylorbear on 2008-01-01
This is very strange.

I have a Logitech G15 keyboard... when i installed Ubuntu and for the first few days of use, everything was flawless.  (I should note that i dual-boot Ubuntu with Vista and use GRUB to select my OS)

Then suddenly today GRUB stopped recognizing my USB keyboard and defaulted me into Ubuntu every time.  So I started reading around online and found where many people suggested changing the BIOS settings to enable legacy usb support.  

I thought this very strange since I hadn't tinkered with BIOS any and didn't have any problems before.

So I started thinking... what was different about my system yesterday that wasn't the same as today... then it dawned on me -- my usb thumb drive!

So here's the kicker:  Without my thumb drive plugged into the front of my keyboard, GRUB fails to detect my USB keyboard.  WITH the thumb drive plugged in... it works fine.

Whats going on here????????

---

### Post by baylorbear on 2008-01-02
I gotta bump this... i seriously need help with this one...

---

### Post by at0myx on 2008-01-02
Did enabling legacy usb support let you use grub without the thumb drive?

---

### Post by baylorbear on 2008-01-03
Nope.  Unfortunately legacy usb did nothing for me.  Still only works with the thumb drive in place...

---

### Post by mangoes on 2008-02-07
I have a similar problem. I have logitech usb keyboard and mouse with receiver station. They work fine except during grab session.

But something is even weirder:
GRUB could recognize my keyboard after I enabled usb keyboard/mouse support in BIOS, but if I choose ubuntu as OS,  the computer keeps REBOOTING.

Anyone know what's going on?

---

