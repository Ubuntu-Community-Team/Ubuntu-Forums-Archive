---
title: "Windows 10 + Ubuntu dual - Gigabyte mb - a fix for USB keyboard disabled in GRUB menu"
date: 2019-10-06
forum: Installation &amp; Upgrades
---

### Post by nsecomb on 2019-10-06
I know that a number of new Ubuntu users installing Ubuntu after Windows 10 have reported that their USB keyboard isn't powered when GRUB displays its boot options (Ubuntu, Advanced options..., Windows etc), and in the last 2 days I was one of them.

This post descibes the (relatively) simple fix that worked in my case. I'll jump to the fix, and then describe the situation I had, what approaches didn't work, and how I got to the fix.

_Fix_: in BIOS, change BIOS Fast Boot from "Ultra Fast" to "Enabled", save and reboot.
_Reason_: I suspect Gigabyte's "Ultra Fast" setting for Fast Boot delays the activation of the USB slots until after the point where the OS is selected.
Note: this fix is fairly specific to Gigabyte motherboards, but motherboards from other manufacturers with something like the "Fast Boot" feature might also be able to use this fix.

_System Components_:
Hardware:[INDENT]Gigabyte X399 Aorus Extreme motherboard
Thermaltake Core W100 case
USB 2.0 Keyboards: Microsoft Wired 600, Logitech K120
USB 2.0 flashdrives: generic 4GB, sandisk 32 GB
[/INDENT]

Software:[INDENT]Windows 10  v1903
Ubuntu 18.04.3 LTS
[/INDENT]

_Preceding Installation_:
[LIST]
[*]Downloaded Gigabyte App Center, and used Fast Boot app to get into the BIOS (because even before installing Ubuntu, DEL key was not opening BIOS during boot) 
[*]Had created a [FONT=&amp]bootable [/FONT]Windows 10 [FONT=&amp]USB stick.[/FONT] 
[*]On one of my other PCs had created a [FONT=&amp]separate bootable Ubuntu ([/FONT][FONT=&amp]18.04.3 LTS) USB stick with Rufus.
[/FONT] 
[*][FONT=&amp]In BIOS, changed the sequence of drive checking for boot so that it read from the USB stick first.
[/FONT] 
[*][FONT=&amp]Successfully installed [/FONT][FONT=&amp]Ubuntu 18.04.3 LTS using the [/FONT][FONT=&amp]bootable [/FONT][FONT=&amp]USB stick:[/FONT] 
[/LIST]
[INDENT][FONT=&amp] - installed alongside Windows 10
- used manual partitions tool
[/FONT][/INDENT]
[FONT=&amp]
_The Issue_: When GRUB's options popped up about what OS should be booted to, and asked for the arrow keys to be used to move between options, none of the keyboard keys worked. AND, because none of the keys were working, the system couldn't be forced into BIOS to check or change configurations such as USB support.

_What attempted fixes did **not **work_: (assume attempted fix = change and reboot to see if fix worked)
[/FONT]

[LIST=1]
[*]using any of the other USB slots on the case 
[*]using a different USB keyboard (the Core W100 does not have PS/2 slots) 
[*]inserting the [FONT=&amp]bootable [/FONT]Windows 10 [FONT=&amp]USB stick[/FONT] 
[*]inserting [FONT=&amp]the [/FONT][FONT=&amp]bootable Ubuntu [/FONT][FONT=&amp]USB stick[/FONT] 
[*][FONT=&amp]extending the selection time in GRUB from 10 seconds to 40 seconds to give the system more time to recognise the keyboard[/FONT] 
[/LIST]
[FONT=&amp][FONT=&amp][U]
The actual fix[/U]: (in my case)
[/FONT][/FONT]
[LIST=1]
[*]In Ubuntu, change the default selection in GRUB from Ubuntu to Windows 10 using these instructions: [HTML]https://askubuntu.com/questions/148095/how-do-i-set-the-grub-timeout-and-the-grub-default-boot-entry
[/HTML] 
[*]After Rebooting in Windows 10, go into Gigabyte's Fast Boot app and select Enter BIOS Setup now (the system will reboot into BIOS) 
[*]Change the BIOS Fast Boot setting from "Ultra Fast" to "Enabled", save and accept changes to the boot managers (the system will reboot again) 
[/LIST]

In my case, this change to the BIOS Fast Boot setting led to the USB keyboard being powered and available when the GRUB menu pops up.

I also then went back and change the GRUB default option back to Ubuntu.


Hope this helps anyone else installing a Ubuntu dual boot alongside Windows 10 who finds they can't use the arrow keys to select which OS gets booted to.


kind regards,

Nigel
[FONT=&amp]
[/FONT]

[FONT=&amp]
[/FONT]

---

