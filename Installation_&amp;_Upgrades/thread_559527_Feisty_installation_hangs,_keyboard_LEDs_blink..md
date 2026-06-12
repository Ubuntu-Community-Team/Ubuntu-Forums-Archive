---
title: "Feisty installation hangs, keyboard LEDs blink."
date: 2007-09-25
forum: Installation &amp; Upgrades
---

### Post by FishFace on 2007-09-25
Hi guys, looks like this is a common symptom.

I've tried disabling IOAPIC in the BIOS, and passing noapic at the boot: prompt already.

Here are my system specs:

MSI K9N Neo Motherboard. Appears to based on nVidia MCP65.
AMD X2 5600
2x IDE Hard Drives
1x IDE CD Drive, connected to a SATA port using a SATA <-> IDE dongle.

I am trying to install (k)ubuntu feisty, using the desktop amd64 iso. The MD5SUM is correct, and the disk appears to have been successfully burnt - it can be mounted and all the files are the correct size, as verified by diff and ls -Rl.

I think I am actually having two different problems. If I try to select any of the options in the menu other than memtest and boot from first harddrive, I get a blank screen. The computer appears to whirr away and do things, but then after a while the caps/scroll lock start blinking and I have to hard reset. I assume this is something to do with the graphics card but I don't know what. For some reason the nvidia driver has started to refuse to load in debian lenny, and I have to use nv, but I wouldn't have thought the installer was trying to do anything fancy. I am getting jittery that I might have fried my graphics card.

Still, I have also tried using the boot: prompt and typing "live vga=771" and that gets my a graphical boot splash with bouncing block. This chunters to itself for a while and it appears that it is just when it changes from bouncing block to progress bar that the thing hangs (and the LEDs blink)

I have also been having trouble in debian, my old system. On bootup, it was spitting out errors to do with my CD drive. To verify that the CD had been burnt correctly I had to use an IDE port instead of the SATA port - but unfortunately this still didn't allow an installation. It appears there is a kernel bug with my motherboard, and possibly with PCI MSI. Upgrading from 2.6.18 to 2.6.21 appears to have fixed the dmesg output, but I've not switched the drive back to the SATA port to verify this.

Any help is greatly appreciated. I want to install quickly since I can then get a 64 bit OS up and running, and see whether I can convince nvidia to load, and thus convince myself that I haven't ended up with a £180 paperweight.

Cheers!

---

