---
title: "Problems Installing"
date: 2007-09-11
forum: Installation &amp; Upgrades
---

### Post by bhackett on 2007-09-11
I tried installing Ubuntu off of the disk, and I get to the menu when booting. I choose to install, and immediately get a black console-like screen with the message:

/bin/sh: can't access tty; job control turned off
( init ramfs ) [ 45.690698 ] ata 2.01: failed to set xfermode [ err_mask = 0x4 ]

Although I doubt that its important, I'm running from a Vista. All of the computer's hardware is, at the worst, six months old. If you need specific hardware information, please tell me what it is and how to get to it. Thank you for your time.

---

### Post by merlinus on 2007-09-11
Post system specs.

---

### Post by bhackett on 2007-09-11
OS: Windows Vista Home Premium
Processor: Intel Pentium 4 CPU 3.20GHz
Memory (RAM): 1023 MB
System type: 32-bit
Graphics: RADEON 9600 Series
Primary Hard Disk: 233GB Free
Media Drives: CD/DVD and CD/DVDCD

If there's anything else you need, tell me. Thanks.

---

### Post by merlinus on 2007-09-11
You might try the Alternate Desktop install cd. It is text-based, but quite straightforward.

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Tick the box below the green Start Download text, then click the text to begin.

Once installed, you can change the driver to vesa from a command line to get to a gui, where you can search for and install the correct video drivers.

Also, before attempting ubuntu install, delete temp and other unneeded files, backup data, set virtual paging to zero (set it back after install), and defrag several times.

Then use vista's disk manager to resize its partition.

---

### Post by bhackett on 2007-09-11
I have two questions.
How would I set virtual paging to zero, and what would that do? Also, how would I use Vista's disk manager to resize its partition? Thank you for your help.

---

### Post by merlinus on 2007-09-11
Virtual paging leaves a large block of system files at the end of the hdd, so you cannot shrink it as much as if it is set to zero temporarily.

Since I avoid M$ like the plague, you will have to search vista help for info on that and its disk manager, although I would imagine both would be found somewhere in the System Tools menus.

Be sure to go through the other steps outlined in my previous post before resizing.

---

