---
title: "Can't start ubuntu instalation!"
date: 2008-11-21
forum: Installation &amp; Upgrades
---

### Post by dj_ee3 on 2008-11-21
I can't install ubuntu... when I press install from the bootable disc menu a error pops up
The error is: 
[ 31.661348]Acpi: Unable to load the system description tables
[ 31.793648]..MP-BIOS bug: 8254 timer not connected to IO-APIC
[ 32.013883]Kernel panic - not syncing: IO-APIC + timer doesn't work! Boot with apic=debug and send a report. Then try booting the `noapic` option
Have in mind that I am a beginner so explain simply what I have to do.

---

### Post by oilchangeguy on 2008-11-21
> **dj_ee3 said:**
> I can't install ubuntu... when I press install from the bootable disc menu a error pops up
The error is: 
[ 31.661348]Acpi: Unable to load the system description tables
[ 31.793648]..MP-BIOS bug: 8254 timer not connected to IO-APIC
[ 32.013883]Kernel panic - not syncing: IO-APIC + timer doesn't work! Boot with apic=debug and send a report. Then try booting the `noapic` option
Have in mind that I am a beginner so explain simply what I have to do.

please provide your system specs. cpu speed, amount of ram, and hard drive size.

---

### Post by dj_ee3 on 2008-11-21
My computer is acer AM1641-U1521A which comes with windows vista (which I don't want) 2 gb ram 320 gb hard. I read a little bit of the forum about that problems and I found a solution which is to turn off the southbridge ACPI HPET Table which actually make the instalation pass this error but in the processes after this cause another error to come up on screen and the error is  Buffer I/O error on device sr0, logical block 53603. I have used ubuntu before on my pc and the only thing I had to do before instalation is disable acpi because of a bluetooth error and everything was fine but now, I don't know what to do... so HELPPP

---

### Post by luckis on 2008-11-21
Dear dj_ee3, on my box the device sr0 is the dvd/cd-rom...so if this is your case too this means that you have a faulty burn and need to re-burn the image...to test that just do the check in boot...always do that on fresh installs saves a lot of time! :P

---

