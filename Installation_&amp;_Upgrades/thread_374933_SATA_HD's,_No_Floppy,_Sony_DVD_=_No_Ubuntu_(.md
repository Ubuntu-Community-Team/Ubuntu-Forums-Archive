---
title: "SATA HD's, No Floppy, Sony DVD = No Ubuntu :("
date: 2007-03-03
forum: Installation &amp; Upgrades
---

### Post by LzIeNuUsX on 2007-03-03
My goal is a Dual Boot Windows XP MCE and Ubuntu system.

I tried to install Ubuntu 6.06 LTS from the Official Ubuntu book DVD and I get the "no common cd-rom drive" message.  I downloaded and tried the Ubuntu 6.10 alternative cd as well.  I even tired the latest Knoppix 5.1.1 live cd (I get the "can't find knoppix filesystem".  Fedora 6 fails as well ("PCI: BIOS Bug: MCFG area at f0000000 is not E820-reserved").

My system is a brand new build:
Intel DG965OT mobo with E6600 Dual Core 2
2 SATA 250GB drives running as RAID 0 using the Intel Matrix RAID drivers
NO FLOPPY DRIVE
SONY DRU-810A DVD-RW
1 GB of RAM
Windows XP MCE is my first partion it installs fine. 

From my research online:
I tried different BIOS settings.
I wiped my RAID and just installed Windows on just one drive then put the Ubuntu DVD in - same errors
I even tried different optical drives from my other machine which Dual Boots WinXP and Ubuntu just fine. Its a stock DELL Dimension 8200.

Since I have watched the install several times it first is searching(?) for floppy drivers the it goes into the "no common cd-rom drive" message.  Since there is NO FLOPPY does it get confused?

I was (and still am) expecting to run into some problems with the Intel RAID but with at least the Ubuntu I don't get that far.

No sure what to try next.

---

### Post by bullgr on 2007-03-03
hi...

i update yesterday my pc (core2duo 6300) and had the same problem...
follow this steps and i believe your fine with that

-in the motherboard bios in the SATA Configuration make the selection to see the system
the SATA like IDE. in my motherboard the option is "Enhaced". after that, the system
handles the SATA devices like IDE.

-download the last Ubuntu version (Edgy) and boot from the cd (check the boot priority
in bios). if it boot's (like in mine), you can install ubuntu.

hope i help...

---

### Post by LzIeNuUsX on 2007-03-03
bullgr,

Is your system dual boot?

---

### Post by LzIeNuUsX on 2007-03-05
I don't have that "enhanced" BIOS setting availble to me.  Just for a sanity check I killed my RAID array, looked for that BIOS setting and tried to install ubuntu but I got the same "no common cd-rom drive found" message even on a non RAID system.

I am stubburd and still want get a dual boot system WinXP MCE and Ubuntu running on RAID0 SATA drives.

I have done more searches online and it seems my mobo (Intel DG965OT) with the Core 2 Duo is a problem.

Has anyone successfully installed Ubuntu or any Linux on an Intel DG965OT board?

---

