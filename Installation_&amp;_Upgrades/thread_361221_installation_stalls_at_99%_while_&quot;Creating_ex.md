---
title: "installation stalls at 99% while &quot;Creating ext3 file system..&quot;, on a HP dc5750"
date: 2007-02-14
forum: Installation &amp; Upgrades
---

### Post by sailorfej on 2007-02-14
I am trying to install kubuntu on a brand new HP dc5750.

The live CD loads, and I am able to start and progress through the installer up until it trys to create the ext3 file system on partition 1:

after selecting the erase the entire disk I get the "Ready to Install" window, the installer starts, at the "Creating ext3 file system for / in partition #1 of IDE1 master (hda)..." stage, the progress bar runs fairly quickly until it reaches 99%, then it stalls, at that point the disk activity light still blinks intermittently, but nothing happens.  At this point the system is not frozen, but responds very slowly.

I should also note that at this point I was going try to get a dmesg dump and copy it to another machine to include in this post when I realized that in the network card (Broadcom 5755 Gigabit Ethernet) is not being detected.

I have tried several iterations of the BIOS settings, including legacy, native, and RAID modes on the SATA controller, currently I/O APIC is disabled in the BIOS, I had trouble booting with out disabling I/O APIC either in the BIOS or by adding noapic to the kernel line during boot.

I have tried Edgy also, but it will not even boot, the initial boot menu loads, but the kernel load fails.

Here are the machine specs:

HP dc5750s/A6435
BIOS: 786E3 v2.10
CPU: AMD64 3500+
Chipset: ATI Radeon XPRESS 1150
SATA HDD and DVD
NIC: Broadcom 5755
Video: Integrated ATI Radeon X300 graphics

Any help and/or advice, especially if you have successfully installed on this machine, would be greatly appreciated.

Thanks,
Jeff

---

### Post by sailorfej on 2007-02-14
Crap,

Never mind, it just successfully progressed past that point while I was typing the post, I actually let it sit longer a couple times before, but this time it is working.

curiouser and curiouser

Comments will still be welcome, and any ideas on getting it to detect the Broadcom 5755 card.

Thanks,
Jeff

---

### Post by sailorfej on 2007-02-14
Double crap,

I was wrong it is still not working, the last two attempts stalled while copying files, it definitely does not like the SATA controller, and this thing does not have a standard IDE controller at all.

To recap,

first error was:
"MP-BIOS bug: 8254 timer not connected to IO-APIC"

disabled APIC in bios (noapic on kernel line also works), proceeded to load live but does not detect sound or network card, lots of weird errors in dmesg, including one that even said "weird error: cpu not detected in bios"  and "system bus detected: 33 Mhz" (am I suddenly running a 486?).

installation stalls when during either ext3 file system creation or when copying files immediately there after.

I have tried several bios setting changes including:

SATA controller mode: legacy, native, and RAID

BIOS DMA Data transfers: enabled and disabled

HDD translation: auto, LBA assisted, and Bit transfer

Data Execution Prevention: enabled and disabled

OS management of Embedded Security Device: enabled and disabled

Please any suggestions would be greatly appreciated.

---

