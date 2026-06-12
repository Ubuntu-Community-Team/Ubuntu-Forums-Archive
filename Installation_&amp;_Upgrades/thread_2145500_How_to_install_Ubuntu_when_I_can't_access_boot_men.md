---
title: "How to install Ubuntu when I can't access boot menu"
date: 2013-05-15
forum: Installation &amp; Upgrades
---

### Post by joemolo on 2013-05-15
Hi All,
Here is my current situation:
I got given an hp compaq presario cq70 by my uncle because my cousin smashed it when he fell out with his girlfriend. It looks like junk, the screen is attached to the main body of the laptop only by a few cables. However it does power on well and loads up windows vista. It has 2gb ram and a 2.0ghz processor so it's not horrendously slow but windows isn't doing it any favours. I've decided to put ubuntu onto it.

The problem is that the only way of having a screen is by attaching it to a monitor via a VGA cable. Unfortunately I don't see anything on the screen until windows loads up, meaning obviously that i am unable to get to the boot menu to enable me to load ubuntu from my usb stick. I thought about downloading the WUBI.exe installer but I think you still end up having to operate the bootloader after it reboots.

Does anybody know how I can get around this problem?

Thanks a lot

---

### Post by mr_mop on 2013-05-16
All I can suggest is you go through a few boots and tap rapidly on a different key each time to see which one will get you in the BIOS
Esc, F1, F2, F10, F12

Having read a few pages, F1 and F10 seem most likely candidates, so maybe try those first.

Once its going to the BIOS it might show on the correct screen.

---

### Post by Mark Phelps on 2013-05-17
Vista is one of the classic "fails" for MS.  When it came out, there were only Beta drivers, and it used resources like crazy.  Win7 has improved considerably on that, has real drivers, and uses a lot less resources.

There is often a way, on laptops, of using a key combination to force the video to come out the video jack (typically) on the back, instead of the screen.  This is used when folks connect projectors to their laptops.

If you don't know what that key combination is, you can do a Web search for a user guide for this model and in there, it will tell you the combination to use.

If you press that combination during boot, with the external monitor connected, you should be able to continue the boot process.

---

### Post by joemolo on 2013-05-17
Thanks for the suggestions, i managed to access the bios with f10 and change the boot order to boot off a usb stick, whilst holding a torch over the screen (i think something to do with the backlight on the display is broken).

My only problem now is a lack of drivers for the HP w19e monitor :(

---

### Post by Mark Phelps on 2013-05-17
> **joemolo said:**
> ... My only problem now is a lack of drivers for the HP w19e monitor :(

Monitors don't need drivers.  

If you're having problems with the monitor, you should start a new thread for those in the Video section.

---

