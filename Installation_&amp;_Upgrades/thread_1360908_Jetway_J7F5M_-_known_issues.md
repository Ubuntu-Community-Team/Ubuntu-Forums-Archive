---
title: "Jetway J7F5M - known issues?"
date: 2009-12-21
forum: Installation &amp; Upgrades
---

### Post by Tunari on 2009-12-21
Hi everyone!

For 3 days now I've been unsuccessfully been trying to get this small mini-ITX system started, and I'm reaching the end of my rope. Hence I turn to you good people to see if this motherboard/chipset of mine is actually a known trouble maker.

Description of problem:

Installation gets stuck, Ubuntu PenDrive gets stuck on boot. What what little I have managed to gather, the former seems like an issue recognizing the SSD, the latter might be inability to mount persisten drive image, perhaps. Memory test passes OK, but beyond that, I've gotten nothing else to work properly.

**Before going into individual error message and such, I would like to probe if this particular product is not even supposed to work with Ubuntu/Linux in general?**

[http://www.jetwaycomputer.com/J7F5M.html](http://www.jetwaycomputer.com/J7F5M.html)

Jetway J7F5M-VDE 1.2GHz Fanless Hybrid Mini-ITX Motherboard
Processor: VIA Eden 1.2
Chipset: VIA CX700M single chipset
    Memory: 1 x DDR2 533 DIMM slot (512MB)
Graphics: VIA UniChrome&#8482; Pro II Integrated Graphics Core


Thank You very much in advance!

---

### Post by Tunari on 2009-12-21
I'm guessing mini-ITX boards aren't commonplace so I may be hoping too much in hearing "yay" or "nay" experiences on this :)

I did get one suggestion; try DOS (and flash the BIOS). FreeDOS booted (refreshing to have something, anything start up actually...) and I flashed the BIOS.

Much to my astonishment Ubuntu netbook remix started up from 2GB USB pendrive! Desktop isn't working, but that's another story.

[I]Unless I hear otherwise, based on this I am assuming this motherboard is supported by Ubuntu, and continue from there.

[/I]EDIT: I would have liked to tag this thread as "SOLVED", but I can't seem to find any way to do this. So this has to stay as-is, I guess...

---

### Post by Tunari on 2010-01-08
I just want to add one more note here, for anyone that may find this thread looking for answers in similar questions.

Main problem for me has been Samsung USB CDROM. I did flash my BIOS to version R06 (latest BIOS version at the time of writing) that supposedly addressed whatever problem (not specified what problem exactly) there has been. However, as long as the unit is attached, various severe problems keep occuring making the system unusable.

I purchased SATA CDROM and managed to try various distributions without the forementioned problems.

However, netbook remix doesn't work properly in this hardware. Most notably the desktop interface is dead/stuck and something seems to slow the system down that I cannot identify, yet anyway. Regular desktop Ubuntu works leaps and bounds better (read: without problems and faster).

If you have found this via search engines, please note dates and versions applicable for this thread...
(Ubuntu 9.10)

---

### Post by fopetesl on 2010-01-09
Yah, Tunari. I'm having the same problem with a Jetway NF94-270-LF Mini-ITX board.
XUBUNTU recognises the Realtek RTL8111C NIC and I can get Internet connection,(all other distros won't out of the box).

But the graphics! Let's just say the driver is wrong for the VIA Unichrome Pro IGP chipset. :(  Tho' according to the spec sheet the board has an Intel GMA950 Graphics core.

Maybe we can use the Windoze driver but I don't know how.

Help!

---

