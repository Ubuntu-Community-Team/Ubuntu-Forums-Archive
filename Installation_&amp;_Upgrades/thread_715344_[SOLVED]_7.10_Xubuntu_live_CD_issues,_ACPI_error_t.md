---
title: "[SOLVED] 7.10 Xubuntu live CD issues, ACPI error then, unable to load system descript"
date: 2008-03-04
forum: Installation &amp; Upgrades
---

### Post by Jon_J on 2008-03-04
The original title **7.10 Xubuntu live CD issues, ACPI error then, unable to load system description table** was too long, so I modified it.
**See post #4 for the solution I found.**
I'm trying to get xubuntu to install/load on an old PC. It currently runs Win98SE fine.
When I first tried to use the live CD, it failed with the following error, 
and checking the CD integrity gives the same error.

**[0.000000] ACPI: BIOS age (1997) fails cutoff (2000), acpi=force is required to enable ACPI**

I made sure both copies of this CD and the ISO file were OK. I checked the MD5, it was OK.
I tried it in my newer computer and Xubuntu loaded and both CDs checked fine.

I later found out how to load acpi=force into the boot options section using F6

Now I get the following error and eventually "Kernel panic"

**Unable to load system description tables**

How do I get past this last error?

Below is a description of this old PC.
```

Video: Sis620 Onboard
Processor: Pentium III 600mhz (Intel)
Mem Ram: 256mb pc100
Motherboard: PCChips (M748LMRT)
20GB HDD
      
BIOS Type                AMI (09/14/01)
BIOS Properties:
      Vendor                   American Megatrends Inc.
      Version                  62710
      Release Date             07/15/97
      Size                     256 KB
      Boot Devices             Floppy Disk, Hard Disk, CD-ROM, ATAPI ZIP, LS-120
      Capabilities             Flash BIOS, Shadow BIOS, Selectable Boot, EDD
      Supported Standards      DMI, APM, ACPI, ESCD, PnP
      Expansion Capabilities   ISA, PCI, AGP, USB

Display:
      Video Adapter            SiS 620  (8 MB)
      3D Accelerator           SiS 86C306
```

---

### Post by Jon_J on 2008-03-04
bump
I updated my PC specs, the old description seemed too complex

---

### Post by Jon_J on 2008-03-05
I downloaded the Alternate Disc ISO to see if that would work. (xubuntu-7.10-alternate-i386.iso)
I checked this newly burned disc on a new machine and the "Disc Integrity" is fine.

I loaded it into the above old machine and select "Install in text mode"
I'm getting the exact same errors as in my first post.
**[0.000000] ACPI: BIOS age (1997) fails cutoff (2000), acpi=force is required to enable ACPI**

Then I use F6 to load **acpi=force**
I now get this error:
**Unable to load system description tables**

What can I do to get past this last error??

EDIT:
I already have the latest BIOS upgrade that can be found, and installed it on this old machine.

---

### Post by Jon_J on 2008-03-05
After much searching I found this solution to my **ACPI: BIOS age (1997) fails** error.
Go into your BIOS, locate the 'Power Management' section, and enable ACPI.

I didn't see "ACPI" at first, but enabling the first setting (Power Management/APM) shows **ACPI/APM**
I then loaded my alternate disc and hit F6, then added **acpi=force**
Now xubuntu trys to install, but I seem to have a CD or CD-ROM drive problem.
I checked all my xubuntu CDRs on my new machine and they all passed the "Check Integrity" test.
On the old computer, all these CDRs FAIL the "Check Integrity" test.
I tried cleaning the lens with a "Lens cleaning CD"
Or maybe these new TDK 52X CDRs are not compatable with my old Toshiba DVD-ROM drive. (I burned at 4X)
BTW, I haven't had any problems with my CD burner. All my CDRs I have burned up to now work fine, except these.
I have some ubuntu 5.10 pressed CD-ROMs. I'll try the install disc of this next....

---

### Post by diegogarcia666 on 2008-05-25
Good morning (for Argentina ;-)).
I'm the same problem wyth my old first PC (:'().
I have an M748LMRT motherboard with a Celeron 433 Mhz processor.
In the last weeks i'd tried several times to install Xubuntu 8.04, both ith the desktop and alternate cd, but was a waste of tine.
the cd says I have an "integrity problem" with the cd.
The cd was checcked 4 times.
Actually i've install with the same cd on other machines....
How can i fix the problem????
I rally want to give my system live with Xubuntu (and the hard is capable....)
My compuer is al right, 'cause i had  an ETCH (Debian) intalled.

Thanks for he help.

---

### Post by JohnnyNova on 2008-07-01
Hi Jon_J,
thank you for your hint about the 'ACPI error then, unable to load system description table' problem with the Powermanagement settings in the BIOS.
This was also the soluton on my Dell Optiplex GX1.
Thanks,
Hans-Jörg

---

