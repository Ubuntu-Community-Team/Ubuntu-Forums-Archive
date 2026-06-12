---
title: "&quot;Timer not connected to IO-APIC&quot;"
date: 2007-07-21
forum: Installation &amp; Upgrades
---

### Post by RubberSideUp on 2007-07-21
Ok, so i'm trying to install ubuntu (latest version from the website last night). First off i attempted to install the 64bit version, it loads the start/install screen and then when i try to actually install, it loads a few lines of text then the screen goes blank and thats the end of it, nothing happens whatsoever.

So i gave up on 64bit and downloaded the standard version. Start/install screen shows up and when i attempt to install it loads for a couple of seconds then i get the following error.

[24.116114] MP-BIOS bug : 8254 Timer not connected to IO-APIC
[24.2950523] Kernel panic - not syncing: IO-APIC + Timer doesn't work! Boot with APIC=debug and send a report. Then try booting with the "noapic" option [24.295092]

Can anyone help? i'm a complete linux novice, and its fustrating not being able to get anything running :(

Cheers.

---

### Post by roaldz on 2007-07-21
Hey,

If you get the bootloader (the part where you can choose if you want to start/install ubuntu) in front of you, press F6.

Now you'll see a line containing words like "casper" and "kernel" in the bottom of your screen. Go to the end of that line by keyboard and remove the words "quiet splash". Then add "noapic nolapic" at the end of the line and try booting again (by pressing enter).
If it fails again, give us the output so we can diagnose the problem.

Good luck!

Roald

---

### Post by RubberSideUp on 2007-07-21
Ok, so i got it to install :) Thanks for the help!!! 

Now i've got another problem. 

i can't boot into linux, theres no option.. pc goes to the bios screen and just boots straight into windows. Could that be because i installed linux on a different hard drive?

Anything in particular i should do to get it to give me the dual boot options?

Cheers!

---

### Post by Pumalite on 2007-07-21
Where did you install Grub?. In the installation process, step 7, Advanced Tab allows you to determine where you want Grub installed. Normally is to MBR if you want your Grub to appear at boot. (hd0,0)

---

