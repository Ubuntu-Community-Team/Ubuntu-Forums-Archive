---
title: "Ubuntu Grub 17 error at Grub 1.5"
date: 2004-12-15
forum: Installation &amp; Upgrades
---

### Post by javabiz on 2004-12-15
I solved this but I'm not sure which fix was the one that got it going!

First, I set disk bios to NORMAL as opposed to LBA because when the initial bios display screen came up after the ram check--it showed a 512 MB hard drive.   After setting the drive configuration to NORMAL it showed 15 GB--which was more like it.

Next, I booted the Ubuntu CD and customized the partitioning to something like this.
0-1023 Boot partition with no mount (it used 1 MB for this)
1024 to the swap 500 MB starting point was mounted as /

When the first stage was finished--it booted right up to the next install phase.  After that it completed successfully and rebooted into the gui login splash screen.  However, I had no serial mouse yet--due to a bug--I found a page on the internet on how to solve this problem!

[url]http://ubuntuforums.org/archive/index.php/t-3839.html[/ur

So does anyone--know which step actually solved the error 17 problem--or did both do the trick?
Postupdate: Mouse Problem
Finally got it working with a very old Logitech serial mouse.  Turns out when I followed the url above it told me to go through the instructions.  When I got to the part where you pick the mouse--I picked Logitech--logically-RIGHT!  This turned out to be wrong because this choice evidently was for the newer Logitech serial mice.  I changed my selection  to AUTO (for the mouse type) and continued following the directions verbatum--and it worked fine!

---

### Post by wallijonn on 2004-12-22
[QUOTE=javabiz]So does anyone--know which step actually solved the error 17 problem--or did both do the trick?[/QUOTE]

Your setting the disk drive type to Normal probably did the trick.

It isn't so much that LBA / Normal / CHS is the problem, it is what the disk drive was originally formated for that causes the problem. Even though it says LBA, when you format a disk for Windows it will use CHS (Cylinder/Head/Sector). And even that is not the problem - it's how it writes the HD ID tag (disk label). On most installs you can leave it blank (like Windows98) . But even when it is blank it will be formatted in a certain way.

The same thing happens when you format a new HD under Linux. Linux will assign an ID tag (label) to the HD. If you tried to re-format it for Windows it may not work. You will have to use Linux's fdisk program to delete the partirions, write it out to disk, and then wipe out any HD label (tag) assigned to it before it can be formatted for Windows.  

Basically by changing it from LBA to normal you told the BIOS to clear out its table, to ignore the MBR record, and most importantly, if it was previously formatted with WXP, to clear out the ACPI table. 

If you install WXP, then remove the ribbon cable, set the BIOS IRQs manually, save the settings, and then reconnected the IDE cable (without booting the OS), you should find that the IRQs have been set to what they were with WXP. 

This is why I set my IRQs manually before installing any OS. Even though WXP will ignore the IRQ map in the BIOS it won't then save its settings to the HD boot record. I can then go and dual-boot the HD.

---

### Post by wallijonn on 2004-12-22
Strange. An 8 with ) will cause a smiley.

Windows 98
Windows 98)

8 ) = 8) {no space between the "8" and the ")"}

---

