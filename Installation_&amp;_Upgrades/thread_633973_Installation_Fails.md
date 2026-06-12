---
title: "Installation Fails"
date: 2007-12-07
forum: Installation &amp; Upgrades
---

### Post by sgeoxd on 2007-12-07
I've used Ubuntu in some form on/off for awhile now and have never had any major problems I couldn't resolve through some research or toying around...until now.  

After years of ragging, I recently I talked my old Electrical Engineer step dad into trying Linux and naturally recommended Ubuntu.  He purchased an IBM Netvista 6578-MYU off ebay to play with and ordered a CD. Everything seemed great until we tried to install the system.  

Anytime we try the install via the install/live option for the x86 version of Feisty Fawn ordered through shipit a window will appear indicating the Kernel is loading.  It reaches 100% then disappears.  The monitor will sometimes go to a blank screen with a flashing cursor in the upper left corner. It may do this for a few seconds (or not at all) before the monitor indicates there is no longer a connection to the Video Card and blanks out.  At no point after the Kernel Loading message will it display any text or other characters and there is no change at all (even waited overnight once) like it were just running abnormally slow.

Well, he gave up and gave me most of this PC.  Over the past few months, on and off, combined we have tried the following steps during the course of working around this (in no particular order):
- Verified the shipit disc works fine on a different PC via the Live/Install option.
- Tried 3 different NVIDIA based video cards (1 PCI, 2 AGP) in addition to the onboard.
- Swapped the VGA cable between the onboard and added video cards to make sure it didn't boot on one and switch to the other.
- Turned the monitor off/on.
- Ran a verification of the install disc from shipit via the boot menu option.
- Tried a  downloaded version of Feisty Fawn that was verified via MD5 Checksum and the boot menu option.
- Used 3-4 different monitors.
- Defaulted all BIOS settings.
- 4 different Hard Drives (on different iDE buses, both primary and slave).
- Swapped out the CD ROM Twice.
- Tried different IDE cables.
- Updated the BIOS to the latest version.
- Downloaded the server version of Gutsy Gibbon - verified via MD5 Checksum and the boot menu option on the disc itself.
- Tried 3 different memory modules seperatly and in combination (1-512MB, 2-64MB all of different OEM)
- Ran a memory test overnight on all the available memory - with no errors.
- Disabled APM, ACPI, unnecessary ports, etc. via the BIOS.
- Removed unnecessary hardware i.e. modems, NIC, sound, etc.
- Installed Windows 98 and XP to verify the system functions normally with different OS's.
- Tried the text install on the Alternate Gutsy Gibbon disc. Downloaded then verified via MD5 Checksum and the boot menu option on the disc.

So, summary version. Different discs and versions (including text install). All new hardware except the MOBO. Played with BIOS settings and updated that.

At this point I mostly want recommendations and second opinions on the next step.  I haven't played with too many Kernel options and that is likely what will need to happen.  One suggestion is to use "acpi=off pci=noacpi pnpbios=off vga=0x317"  Should that work and/or are there different options that should be tried.  Otherwise, I was thinking of trying to install via KNOPPIX.

Hopefully that covers it.  It'd be nice if I missed something that may get it up quick and easy ;)  It's become a personal mission one way or another to demonstrate how well this can work compared to what he's been accustommed to with DOS/Windows.  Thanks to all those who help in this community ahead of time!  Even without ever posting before you've always been most helpful.

---

### Post by Pumalite on 2007-12-07
Post your specs. How much memory do you have?

---

### Post by sgeoxd on 2007-12-07
This was duplicated with 64MB, 128MB and 512MB RAM.  All of which are above the minimum requirement for Gutsy Server as far as I know.  Although I could understand if 64/128 didn't work on the Live CD version.

The onboard Video Card is weak at 1MB.  The others tried were 32MB and 64MB.  All NVIDIA chipsets.

Although the GUI install failed, at this point this machine will be dedicated for server use.  So I don't need a GUI install or GUI at all.  That's why I tried the Server and Alternate install CD's.

Once up this machine won't have a CD Drive, Keyboard, Mouse, Monitor or much else connected to it outside what is required to operate a LAMP server with admin being done via SSH. 

Currently what's loaded:
2 10GB Hard Drives, both Maxtor and enabled as Master's.
1 48X CD-ROM as the Primary Slave.
2 64MB sticks (128MB) of PC100 RAM.
64 MB GeForce II MX Video Card
Linksys NIC (did try without the NIC as well for the install as well).
1 GHz processor

---

### Post by Pumalite on 2007-12-07
Try the CD's in a different computer. It could be a bad burn. Did you do md5sum?
Clean the lens in your burner.

---

### Post by sgeoxd on 2007-12-08
Tried 3 different burned CD's all different versions.
- Feisty regular x86
- Gutsy Server x86
- Gutsy Alternate

All 3 were verified via MD5 prior to burning. Once burned they were re-verified via the boot menu option to "Check for defects".  A 4th was also tried that wasn't burned. It was the regular Feisty from shipit.  

All CD's work normally in a different PC. As multiple CD-ROMs were tried during install on this particular PC, that work normally otherwise (i.e. Windows install and use), I wouldn't think a dirty lense would cause problems.

There was 512MB present when trying to run the normal install.  Currently trying the text install with 128MB on the Alternate.  Same results no matter what combination is tried.

---

### Post by Pumalite on 2007-12-08
Try other Linux distros and see if you are incompatible with Linux in general or Ubuntu in particular.

---

### Post by sgeoxd on 2007-12-20
> **Pumalite said:**
> Try other Linux distros and see if you are incompatible with Linux in general or Ubuntu in particular.

Wow.  That was a good call. The Gentoo minimal install disk and Knoppix both also failed as well.  Went ahead and tried the string "acpi=off pci=noacpi pnpbios=off vga=0x317" with the Alternate Gutsy also with no luck.

Played in the BIOS. Re-verified Mouse, Floppy, Serial Port, Parallel Port, Audio, Virus Detection, and 'Plug n' Play' were all disabled.  Also tried toggling the Video Interrupt to off and changing the IDE detection to 'compatible' from 'optimized'.

After all that there was no change.  I did try the advanced options provided on the Knoppix boot.  Something different there.  When using 'Knoppix 2' for the text install the monitor hangs but hasn't gone to power saving mode.  The 'failsafe' option actually gets past the initial loading of the Kernel. The last message before it froze (been having to hard reboot) was "Checking 'hlt' instruction"

I know not the best place for this question, but has anyone had much experience with the Open Source BIOS's?  Since this thing is somewhat worthless to me now thought I might try that.  May help, may make it worse ;) Worst case I have other hardware to use.  

I'll research that later and sit on it for a few days.  See if any other ideas come up.

---

