---
title: "Installation problems   ACPI"
date: 2008-10-06
forum: Installation &amp; Upgrades
---

### Post by badorset on 2008-10-06
M/B   Biostar 690g
Proc  AMD Athlon X2 3800+
Ubuntu  8.04    Kernel 2.6.24 -16
ACPI  problems at startup ??

After installing OK on old computer I tried installing on my main computer (config above) using a empty
 hard disk in a caddy.
1. Hangs after few seconds with flashing curser and no info.
2.Managed to install by using F6 option and selecting ACPI=off
	appears at this stage to work OK.
3.Reboot to load from hard disk and again hangs with flashing curser.
4.Reboot using recovery option and loading stops after  message
	clocksource TSC unstable  
5 Search on forums suggest  either of following might help
	CLOCKSOURCE=hpet      or
	CLOCKSOURCE=acpi_pm
6. Entered both of above (indivitually) at top of cmd list using the startup options, same result !!

Being new to Linux I have now become stuck!  Am I doing something wrong ? or do I need other parameters ?
Some discussions talk of using older kernel ?  Is this useful and how do I do this ?
Any help would be much appreciated.

---

### Post by Partyboi2 on 2008-10-06
Have you tried booting using one of these boot options
clocksource=hpet
notsc
acpi=off
To do this press "ESC" when you see grub loading... Then highlight the kernel you are going to use and press "e" then highlight the kernel line again pressing "e" and add the boot option to the end and press "enter" then "b" to boot.

---

### Post by upchucky on 2008-10-06
hmm it looks like he said he gets only flashing cursor, if true then grub is not finding the boot sector, if this is true then repair grub by downloading supergrub advanced.

search here for methods to fix mbr and grub edits, plus menu.lst edits

---

### Post by cooke77 on 2008-10-06
Badorset,did you by any chance see this line, during the Start-up (of Grub)......"Press 'ESC', to enter Menu."?

IF you are having a APCI problem, you should use the Menu (to pick the 3rd one...yeah, the one that says (with APCI problems)).
You only have to use it the one time (to get the installation of Ubuntu to progress through the process of loading).
I have a AMD Athlon 64 X2 60000+ CPU, on a MV2-VM motherboard........with a 'APCI problem' (that is, the "APCI setting' in mine is Enabled......the reason 'why' the problem exists, in the first place.)
 I have use both Ubuntu, and Kubuntu...in a Dual-Boot set-up, on my computer (with XP Pro, on a 250 Gig hard-drive......Kubuntu, now, on another 250 Gig (formatted as NTFS)hard-drive, installed via the "Within Windows" option).
Have used this method, many times. With success.
Check your BIOS, you'll find maybe that yours is Enabled, also.
As for the Clocksource 'error'......that could due to the fact that your CPU's Frequency is not SET properly....needs to be.
Check to see if it can SET, via Auto (in BIOS).

If Clocksource 'error' still occurs, would suggest 're-seating' CPU, and Heat-sink....with new application of thermal paste. CPU could be overheating, from being installed incorrectly.

---

### Post by badorset on 2008-10-12
Thanks for all the tips.  
I disabled ACPI in the BIOS and also tried the different parameters suggested but always had the same problem.
As I had a disc of Ubuntu 7.10 64 bit I decided to try this and as the live version worked OK I installed to the hard disk. This also worked OK so tried the online update to version 8.04 and this ran without errors so now I have a working Ubuntu Linux 8.04.
Perhaps, if I had installed the 64 bit version initially I might have saved myself much grief!
   Unlike Windows where i stay with 32 bit for program compatability I can see no reason not to stay with 64 bit for Linux

---

