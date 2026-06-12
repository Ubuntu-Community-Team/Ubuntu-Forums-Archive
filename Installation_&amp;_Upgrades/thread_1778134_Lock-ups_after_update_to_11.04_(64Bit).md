---
title: "Lock-ups after update to 11.04 (64Bit)"
date: 2011-06-08
forum: Installation &amp; Upgrades
---

### Post by Mikjoba on 2011-06-08
lock-ups after update to 11.04 (64Bit)
I recently updated my PC (see specs. below) from a completely stable 10.10 to a problematic 11.04, the problem is that the machine will lock up completely after a few minutes of use, no error messages are displayed, and Ctrl+Alt+F4 has normally no effect, only once have I been able to get to a terminal and shut-down the machine normally, when locked-up the Num Lock and Caps Lock LED's are blinking, now to the really strange part, after a restart from this situation(on/off switch) the machine will work without lock-ups for the rest of a session (2 or 3 hours perhaps).
I thought that the problem was being caused by the video driver( ATI Radeon), but the problem occurs if I use either proprietary or non-proprietary drivers.
The problem can occur in any of the programs I use.
It occurs if I use Unity or the classic GUI
Same thing with or without Compiz.
After a lock-up and restart it has also happened that my theme Ambience has been changed to Clearlooks or back.
Because of the above I have recently made a clean install from a newly downloaded 11.04 CD (complete, including formatting) but the problem still remains! have also Googled but have not found anything similar to this, there is perhaps a log file somewhere that would help but I have no idea which one, would be very thankful for any advice that would help to solve this problem.


Mike

PC specs.
Packard Bell imedia A4240NC
AMD Athlon II X2 240 dual-core.
Ati Radeon HD 4650 1024MB
1TB HDD
4GB DDR2 memory

---

### Post by wildmanne39 on 2011-06-09
> **Mikjoba said:**
> lock-ups after update to 11.04 (64Bit)
I recently updated my PC (see specs. below) from a completely stable 10.10 to a problematic 11.04, the problem is that the machine will lock up completely after a few minutes of use, no error messages are displayed, and Ctrl+Alt+F4 has normally no effect, only once have I been able to get to a terminal and shut-down the machine normally, when locked-up the Num Lock and Caps Lock LED's are blinking, now to the really strange part, after a restart from this situation(on/off switch) the machine will work without lock-ups for the rest of a session (2 or 3 hours perhaps).
I thought that the problem was being caused by the video driver( ATI Radeon), but the problem occurs if I use either proprietary or non-proprietary drivers.
The problem can occur in any of the programs I use.
It occurs if I use Unity or the classic GUI
Same thing with or without Compiz.
After a lock-up and restart it has also happened that my theme Ambience has been changed to Clearlooks or back.
Because of the above I have recently made a clean install from a newly downloaded 11.04 CD (complete, including formatting) but the problem still remains! have also Googled but have not found anything similar to this, there is perhaps a log file somewhere that would help but I have no idea which one, would be very thankful for any advice that would help to solve this problem.


Mike

PC specs.
Packard Bell imedia A4240NC
AMD Athlon II X2 240 dual-core.
Ati Radeon HD 4650 1024MB
1TB HDD
4GB DDR2 memory
Hi, is this a laptop or desktop? Is it possible that your system is getting hot, I know when I watch hulu in full screen mode with my desktop it jumps up 20 degrees. I also know that systems need to be cleaned regularly, my laptop ran hot I cleaned it and bought a cooling pad and I had no more problems, Most issues like this is video driver issues in natty I think. Also people have cleaned there systems and applied clean lube between there cpus and heat sink and it had helped a lot. Also people have had a lot of trouble with the screen saver coming on and sleep mode after a few minutes and setting screen saver and sleep mode to off have helped. I have no other ideas, I hope one of these things help.

---

### Post by Mikjoba on 2011-06-09
It is a desktop machine, about 6 months old, temperature monitor shows same temperature as before upgrade (between 41-43 degrees C) so this is not the problem (no logic either because as stated after a restart the PC will quite often work OK for hours and will show no major differences in temperature).
I also have a sneaking feeling that video drivers are involved, but it was rock steady under 10.10, obviously new drivers under 11.04 could have broken those that worked under 10.10, but if that is the the case have both proprietary and non-proprietary drivers been updated since 10.10?.
Also please note that this machine is not used for any games or other applications that put a heavy load on the graphics card ( mainly surfing the internet, a bit of word processing and some simple digital photograph editing).

Mike

---

### Post by wildmanne39 on 2011-06-09
> **Mikjoba said:**
> It is a desktop machine, about 6 months old, temperature monitor shows same temperature as before upgrade (between 41-43 degrees C) so this is not the problem (no logic either because as stated after a restart the PC will quite often work OK for hours and will show no major differences in temperature).
I also have a sneaking feeling that video drivers are involved, but it was rock steady under 10.10, obviously new drivers under 11.04 could have broken those that worked under 10.10, but if that is the the case have both proprietary and non-proprietary drivers been updated since 10.10?.
Also please note that this machine is not used for any games or other applications that put a heavy load on the graphics card ( mainly surfing the internet, a bit of word processing and some simple digital photograph editing).

Mike
Hi, all I know as far as the drivers are that there are a lot if issues with them in natty, I to had issues with the nvidia driver. I have to use the old driver 173 for my card, or it locked up and a windows would go white.

---

### Post by Mikjoba on 2011-06-22
Some feedback, as mentioned a new installation from CD did not help, because this PC also has built in graphics (not from ATI!) I removed the ATI (after making changes in the BIOS) and rebooted, the problem was still there! so I decided to make a clean install of 10.04 (with the ATI re-installed) and now I am back to a perfectly stable PC/OS!!
I have tried all sorts of things to induce the problem but the machine is rock steady, obviously it would appear to be some other software/hardware that was causing the problem but what we will never know.
One word of warning, I had obviously made back-ups of all my important files including mail from Evolution (using their backup tool) but the file could not be read by the evolution version on 10.04! fortunately I found a solution which was to start the PC from the 11.04 live CD, open Evolution, restore the mail then mark all mail and save as mbox format, this I had to do separately for the inbox, sent, etc.
Once the machine was booted again and Evolution opened I was able to use import to get all my mail back, just had to mark them all as read, I was also able to save and import my contacts in the same manner.
All's well that ends well! but I will not mark this post as solved.

Thanks
Mike

---

