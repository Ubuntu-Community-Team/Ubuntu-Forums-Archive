---
title: "Ubuntu USB problems"
date: 2011-01-27
forum: Installation &amp; Upgrades
---

### Post by jordanC on 2011-01-27
Ive recently  installed ubuntu desktop edition onto my laptop and wanted to give the  netbook edition a go. Ive got the netbook edition on my USB and ive  prioritised the USB as the top start up option in the BIOS, the only  problem is, my system starts up Ubuntu desktop as normal evrytime i  reboot, any ideas?

---

### Post by coffee412 on 2011-01-27
> **jordanC said:**
> Ive recently  installed ubuntu desktop edition onto my laptop and wanted to give the  netbook edition a go. Ive got the netbook edition on my USB and ive  prioritised the USB as the top start up option in the BIOS, the only  problem is, my system starts up Ubuntu desktop as normal evrytime i  reboot, any ideas?

If you can, From when the bios on the laptop boots you might get a boot selection prompt. Select it and force it to boot from the usb and see what errors if any you get. Have you tried that?

---

### Post by presence1960 on 2011-01-27
Some BIOS report a USB/Flash disk as a hard disk. While you are in BIOS check the hard disk boot order. if the USB/Flash disk is listed there move it to the first position in the hard disk boot order. Save changes to CMOS and continue booting.

---

### Post by jordanC on 2011-01-27
cheers guys, ive made the USB top of the list in BIOS but now i get a blank screen with a flashing line in the top left corner. Tried to do it with a cd/dvd and got the same thing. How would i force boot the USB as you mentioned?

---

### Post by tommyss4l on 2011-01-27
I am having a similar problem on my Asus 1018p. I have the boot priority set correctly to boot from the USB and I've tried pushing F10 during start up but the system just goes straight into ubuntu.

---

### Post by shlstrm on 2011-02-17
In the 1018p you should press escape repeatedly during bootup, then you should be able to choose boot devices other than the standard hdd.

To go into bios on the 1018p, press F2 repeatedly during boot. If you're still having trouble with the escape key you could check 2 things:

1. If you're pressing escape and nothing happens, the computer just keeps booting as normal from hdd, go into bios and check under "boot" that the "boot booster" is turned off.

2. Check the drives and see if your usb stick is recognized as a boot option. If you're not able to see it at all, then either the setup of the usb as bootable has failed or the usb stick is just general fail.

* A hint: Make sure your usb stick is not set as "hdd" or anything like that, this usually screws things up.

---

