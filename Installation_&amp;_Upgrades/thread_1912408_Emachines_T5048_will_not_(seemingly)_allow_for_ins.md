---
title: "Emachines T5048 will not (seemingly) allow for installation from live cd"
date: 2012-01-20
forum: Installation &amp; Upgrades
---

### Post by oneiricAdam on 2012-01-20
Hello all. I'm not sure if the issue revolves around trying to install a modern kernel (3.0+) on an older machine, or if something else is going on.

Background/History/Steps: 
1) Had Ubuntu 11.04 on the machine, running fine.  Decided to go with Fresh install using Live CD of 11.10 32-bit.
Result: Live CD would not work, stayed very long time on purple screen, and then went to a black screen with a single blinking white dash at top left. I gave up.

2) Thinking the machine was just "too old" I tried out Crunchbang 10 (statler, debian-based) 32 bit Live CD.
Result: Live CD took me all the way through graphical install, but upon restart of the machine, it would not boot. Stayed hung on "waiting for /dev to fully populate".  I gave up.

3) Tried running same Crunchbang as just a live CD (not installing) -same "waiting for /dev"

4) Swapped out Hard Drive for another HD in working condition. I was able to repeat all 3 above steps, so I ruled out a bad Hard drive.  Created a USB installer (of 11.10 32-bit) on another machine and was able to reproduce Step 1. Purple screen, then blank screen with blinking cursor. So ruled out a bad CD-rom drive. I Gave up.

5) Tried much of the same steps with various versions of Linux Mint (v11, v12, and Mint Debian) all had similar failure results of not booting into Live CD, or not booting after graphical install if it got that far along.

6) Reloaded 11.04 onto the machine and allowed the GUI tools to upgrade me to 11.10 -after reboot, machine hung on purple screen, then produced blank screen with blinking white cursor. I gave up.

7) Downloaded/burned and installed Ubuntu 10.04.3 LTS Desktop edition.  Live CD worked just fine, install went smoothly, and restart + bootup was slow. But it did work.
So, end result, my computer possibly just does not like 3.0 kernel?

Or is there something I need to do differently to get the live CD and other things working so I can have a clean install of Ubuntu 11.10?

Machine SPecs:
Emachines T-5048, 2 gig RAM, 160 gb hard drive. Motherboard & audio & video are all stock, processor is Hyperthreading P4.

? Any ideas - if anyone has any advice, I'll try it out on the spare HD before wiping out 10.04.3 LTS.
Thanks,
Adam

---

### Post by oneiricAdam on 2012-03-07
I'm replying to my own posting to say that the issue has not been resolved, but at the very least **has been determined**.

It's an old machine. It's not a very robust machine. It has ACPI problems that did not seem to be an issue in older versions of Ubuntu.

Thus, going forward, I can run any LIVE CD I desire, as long as I edit the boot parameters, adding **acpi=off** . Upon install to HD, I edit the grub configuration file, adding same, and rebuild grub and that's it.

The unfortunate (but liveable) downside so far is that I have to manually push the power button to turn off the machine.  Other than that, it's quite possible that without ACPI, certain lm_sensor functionalities will not work as expected, but I'm guessing/reaching here.

Take care all - thanks to any/all who have read my initial posting.

Adam

---

