---
title: "Install/Partition problems"
date: 2007-06-24
forum: Installation &amp; Upgrades
---

### Post by onimike on 2007-06-24
Okay, heres the story.

About a month ago, I installed Ubuntu 7.04 (DVD, i386) onto a hard disk that was natively windows xp.

I created a seperate partition for Ubuntu, 40gigs, while windows kept 120 gigs. Everything was fine and all that.

About two weeks ago I upgraded my system, heres the new stuff:
Gigabyte 965p-ds3 mobo
Intel e4300 C2Duo 1.8ghz
2x 1gb G.Skill DDR2
Geforce 7900 GS 256mb ddr3
Wireless card: D-link air plus dwl-g520 rev.B

When starting up with this new hardware, neither Ubuntu nor Windows would load up. SO instead of troubleshooting with no internet connection, I put in the WinXP Home disc, did a format and install.

The thing is, it only touched the windows partition, so the Ubuntu partition for 40 gigs is still there, but I can't seem to touch it. Inserting my Ubuntu DVD (i386, 7.04) will load up the install menu. Selecting install will load up a linux kernel, but on the Ubutnu logo progress bar is hardlocks the system and forces a restart.

It will not load the text installer either.

So what can I do to either go back to my old version of Ubuntu, or wipe it and install a new one?

Thanks in advance.

---

### Post by merlinus on 2007-06-24
Try SuperGrub:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

-merlin

---

### Post by onimike on 2007-06-24
Thanks for that.  The MBR now lets me select to load Ubuntu.

But it still locks at the progress bar.  Launched recovery mode and it seemed to lock also, or it finished... I'm not sure.  It went to "18" in its task list and located my chipset/graphics and then seemed to do nothing.

---

### Post by merlinus on 2007-06-24
At this point, the easiest solution may be to reinstall ubuntu.

Try Safe Video Mode from the live cd.

You will be able to use your existing 40G partition for the install.

Good luck!

-merlin

---

### Post by onimike on 2007-06-24
Trying to do a fresh install locks up at the splash screen (with the orange bar moving back and forth) in both modes.

I removed quiet and splash from the boot line.  It got to Loading Hardware Drivers before it locked/DVD drive LED stopped blinking, the last line:

[79.430728] ACPI: PCI interrupt  0000:05:02.0 [A] -> GSI 18 (Level, low) -> IRQ 20

Same thing in both Start/Install Ubuntu and Save Graphics Mode.

Doing this also messed up GRUB again, so i had to boot from superdisk to get back into windows.

---

### Post by Pumalite on 2007-06-24
It might be time to check hardware and hardware compatibilities.

---

