---
title: "NewB installation, Feisty frozen"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by johnacook on 2007-04-22
Windows user trying to install for first time.
Downloaded ISO, checked, burned to CD, checked again fine.
Using first install choice on splash screen.
Get cool orange slider bar for a minute, then changes to orange / tan blank screen with immovable cursor.

How long should this screen hang? Probably been 60 minutes now...

Thanks for any help!

---------

AMD Athlon 64 3000+
MSI K8n Neo 2.0
1 Gb PC 3200 RAM
NVidea 6600 AGP video 256
Intending to install to spare 60Gb drive (currently formatted w/ NTFS)
NVidea RAID installed, but I'm not using it
Creative X-Fi XtremeGamer
Logitech USB Mouse
ZBoard USB keyboard
On-board peripherals disabled

---

### Post by pepsi_max2k on 2007-04-22
>> How long should this screen hang?

not 60 minutes :|

sounds like a graphics / xserver problem. you could try installing with the alt cd if you like but you may have much the same problem to start off with, and if you've not used configured a linux system from a command line before then fixing it could give you a big headache.

---

### Post by enderokc on 2007-04-22
What you need to do set up your display for it.  try this

when you boot to the CD, and you get to the first options screen (start Install or Live CD). on the bottom of the screen you will see "VGA"

press F4 to change those settings to 1024x768 or something, and then try and boot. it should work that way.

---

### Post by johnacook on 2007-04-22
Tried a few different video settings - same thing.

Maybe it doesn't like my USB Mouse. I'll try using the PS2 adapter and see if I get any farther.

Are there any F keys r other keystrokes I can try to see if it is totally hung? Even the reset button doesn't work. I have to hit the power switch on the power supply to bring it back.

Thanx much grass for your help. I've alway wanted to give Linux a go.

---

### Post by johnacook on 2007-04-28
Is there a way to bypass the graphical installer? I now know how to boot with options, but none have worked. If I could at least boot to the terminal, I might be able to get somewhere . . .

------------------------------------------------------------------------------

Finally fixed. Had to disable most of the stuff in the system BIOS.

---

