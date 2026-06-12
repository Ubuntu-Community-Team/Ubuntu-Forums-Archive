---
title: "update reboot failure"
date: 2015-09-30
forum: Installation &amp; Upgrades
---

### Post by Callmestupid on 2015-09-30
I had an update msg this AM and preformed from the msg. I got to computer needs to reboot. I clicked on the reboot now button. on exit I clicked on the reboot and not the quit button. When computer rebooted first 5 times I only got a white blinking cursor which did not respond to any keystrokes. 6th time It started to reboot, it got to Auto-detect USB mass storage devices and returned 00 USB mass storage devices found and configured.  At this point computer locks up. I have tried rebooting to set-up but does not respond, possibly the USB keyboard not located but does not go to set-up. Computer is and has been locked were it froze last time now for 30 minutes. I have a self built computer MSI K9N  SLI motherboard with an AMD Phenom (tm) 9500 quad-core 64 bit CPU speed 2.2 GHz. There is 8 GB DDR2 800 (unganged mode) additional info as requested. Any suggestions? Computer also has Ubuntu 14.04 LTS 64 bit and Mythbuntu as operating stystem, was booting to the Mythbuntu before reboot.

---

### Post by Bashing-om on 2015-09-30
Callmestupid; Hello;

Perhaps the graphic's driver (proprietary) got broke in the update ?
Booting with the "nomodeset" boot parameter
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
has what effect ?

If you boot with this boot parameter, one could then consider (RE-)installing the proprietary driver against the new kernel build.

[INDENT][INDENT]maybe yes
[/INDENT][/INDENT]

---

### Post by Callmestupid on 2015-09-30
Computer just does a black screen won't even load the motherboard screen. I have also tried to boot to a live CD in both Ubuntu 14.04 and Puppy Linux. Neither would start.

did not get to try the above. 

Callmestupid

---

### Post by Bashing-om on 2015-09-30
Callmestupid; Ohweee, ohweee ...

This situation
> 
won't even load the motherboard screen.

Is long before the operating system is even a thought in bios' mind.


Problems powering up .. maybe you can  clear out CMOS and revert bios to defaults.
Is this a laptop or desktop box - provided info indicates a desktop ?

Might pull the power cord, depress the power switch for a few seconds, pull the battery from the main board for a few seconds, replace the battery ( if fairly new with that original battery) .. then jumper the CMOS pins to revert bios to default.

Power back up and -> 
What does bios say about the voltage levels ?
Fans spin up, disk drives spin up ... DVD drive work now ? 

What happens now when attempting to boot the operating system ?

[INDENT][INDENT][INDENT]ouch
[/INDENT][/INDENT][/INDENT]

---

