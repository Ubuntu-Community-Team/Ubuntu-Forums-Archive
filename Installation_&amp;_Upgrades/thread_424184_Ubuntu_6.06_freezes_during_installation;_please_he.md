---
title: "Ubuntu 6.06 freezes during installation; please help"
date: 2007-04-26
forum: Installation &amp; Upgrades
---

### Post by hurtstotalktoyou on 2007-04-26
Hi, all.

So, I started to install Ubuntu 6.06, but the installation keeps freezing--sometimes at 15%, sometimes at 24%, and sometimes at another percentage I forget.  Usually it's 15%, though.  When it freezes, the system becomes totally non-responsive.  Not even the mouse will move.  Although it has sometimes reached the "copying files" (that quote is from memory, and may not be exact) stage, lately it never gets beyond the "creating ext3 file system" (again, that quote may not be exact) at 15%.

Once the installer freezes, everything locks up.  I can't move the mouse or even eject the CD.  When I tried the "alternate" installation ISO tapping keys on the keyboard would produce nonsensical characters on the display.

**A bad hard disk?**
Now, my first thought was that it was my hard disk.  After all, I am running a super-old 5400RPM PATA 8.4GB pulled from an old Celeron 466 system.  However, I performed an extensive diagnostic, including a surface scan for bad sectors, and everything passed with flying colors.

**Bad memory?**
I ran memtest for a long, long time, and everything seems fine.  I even tried removing one of my DIMMs, but the problem still rears.  I will try the other DIMM soon, just to be thorough, but I'm fairly certain the memory is not the issue.

**A bad installer CD?**
At this point I've tried three different installation CDs--Ubuntu live, Kubuntu live and Ubuntu alternate--and all of them checked out via the self-test diagnostic.  I even burned the Ubuntu alternate at 8x, just to be safe.  The problem still rears.

**So, what the heck is wrong?**
That's the question I need answered.  If anyone can help, please do!

Thanks in advance!

*System specifications:*
Athlon XP 1800+ Thoroughbred
[MSI KT3 Ultra ARU](http://www.msi.com.tw/program/products/mainboard/mbd/pro_mbd_detail.php?UID=11)
256MB (2x128MB) DDR400 @ 333MHz
[Samsung 8.4GB Voyager 6 Plus SV0844D](http://www.samsung.com/Products/HardDiskDrive/LegacyProducts/downloads/sv0844d.pdf)
[Creative SoundBlaster PCI 128](http://ccftp.creative.com/manualdn/Manuals/TSD/2384/AudioPCI128.pdf)
ATI Rage128 GL AGP (ATI Rage Fury)
Realtek RTL8139 NIC
Lite-on LDW-411S

---

### Post by hurtstotalktoyou on 2007-04-27
*bump*

---

### Post by hurtstotalktoyou on 2007-04-28
*bump*

---

### Post by icechen1 on 2007-04-28
what is your processor?

---

### Post by hurtstotalktoyou on 2007-04-30
> **icechen1 said:**
> what is your processor?

Athlon XP 1800+ Thoroughbred

---

### Post by hurtstotalktoyou on 2007-05-02
*bump*

---

### Post by hurtstotalktoyou on 2007-05-02
*bump*

---

### Post by moshuptrail on 2007-05-02
If I told you the video card what would you do?
My 6.06 locks up the same way and I've determined that the cause is my video card and/or the corresponding drivers.  Mine is a much older ATI, but if you start reading posts about video you'll find that Ubuntu doesn't always get along with ATI cards.  ATI drivers?

You have a very new card.  Maybe a newer version of Ubuntu?

Just a thought...

---

### Post by hurtstotalktoyou on 2007-05-05
Actually I have a really old card.  So is Ubuntu not compatible with the Rage 128 Fury?

---

### Post by tgalati4 on 2007-05-05
It could be a mismatch in bus speeds.  You have a powerful motherboard and processor combination with an old video card and disk drive.  Can you go into the BIOS and declock the processor?  Go with 1/2 speed.

My gut feel tells me it is a data bus problem--mixing old and new components.

The other possibility is your power supply.  Put a volt meter on the red and black leads of an unused harddrive power connector.  Do the same with the yellow and black.  Watch the voltage during boot.  You should get a rock steady 5V and 12V reading during the boot process (as far as you can get anyway).

Make sure your machine is clean of any dust bunnies.  Make sure the heatsink is fully seated on the processor with the proper amount of heat sink compound.  If the processor overheats during reboot, it will halt.  And it will do this at random places.

Check the clips on the heat sink.  Make sure they are intact and tight.  If you have a fan on the heat sink, make sure it is clean and running.

Reseat all of your pci cards and ribbon cables.

Good luck.

---

