---
title: "Dell T3500 - New install-desktop shuts down in 3 sec - no boot screen, no USB recog"
date: 2020-06-24
forum: Installation &amp; Upgrades
---

### Post by shivakotha on 2020-06-24
I tried to install Ubuntu 20.04 by following the recommended installation procedure (Rufus boot from USB stick, replace existing windows, reformat disk).  Dell Precision T3500, circa 2010...  
After going through complete Rufus installation (all the steps in installation as highlighted during installation) -  during reboot, desktop computer keeps shutting down within three seconds - no boot screen, no recognizing USB, nothing...  
Any ideas on how to to fix...  Please remember, no boot screen, USB is not recognized...

---

### Post by CelticWarrior on 2020-06-24
Welcome.

Let's get one thing out of the way first. There's no "Rufus installation". Rufus is a tool to make USB installation/live media. If it boots then it's OK and what was used to make it becomes irrelevant.

Now, assuming it was correctly installed, we proceed to troubleshoot the installation regardless of the media used to install. So, did you noticed any issues in the live session?

---

### Post by shivakotha on 2020-06-24
Thank you for helping.
No issues during installation.  After install, required reboot.  Since then, computer shuts off in 3 seconds after pressing power button - there is no boot screen - same thing occurs (I.e. computer shuts off in 3 seconds) even if USB stick is present

---

### Post by oldfred on 2020-06-24
Are you not now able to press f12 and boot flash drive installer in live mode?
Also try full power down, drain any remaining power by disconnecting from mains & hold power switch. Then reboot & press f12 (if that is correct key). 

If you can boot, run Boot-Repair & post link.
Lets see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by shivakotha on 2020-06-24
Thank you for helping oldfred.

Yes - powered off - so there is no power before cycling through F1 through F12 and power button (and others as well - only a single keyboard key at a time).  It is a USB keyboard, so, maybe it is not possible for system to register it in the 1-3 seconds it takes to turn off - lights on keyboard do not show up.

Computer blinks lights, turns off after 1-3 seconds, in every case.  Computer worked fine with windows before I tried to repurpose it - so, not component related.  I just need to be able to get to boot screen.

---

### Post by oldfred on 2020-06-24
BIOS may have setting to allow USB boot and/or USB keyboard & mouse to work.
You need to try to get into BIOS settings. That often is f2.
Best to read manual and be sure what key to press as others may confuse it.

---

### Post by shivakotha on 2020-06-24
Thanks for your prompt response.

I do not think the keyboard is registering - so, cannot actually have Bios work with the F2 key.  Any options to bring computer back to life without a keyboard.

---

### Post by oldfred on 2020-06-24
Not just power off, but cold boot where you also unplug from mains for a bit and drain all power.

---

### Post by shivakotha on 2020-06-25
Yes - did exactly that. No luck.  Is there anyway to get to bios without a keyboard.

---

### Post by ActionParsnip on 2020-06-25
Do you have the latest BIOS? This may help

---

### Post by shivakotha on 2020-06-25
I did not back-up and do not know how to get to it.  Is there a link to help me get started?

---

### Post by oldfred on 2020-06-25
I would then start checking hardware.
See if USB connection is good. Try a different port. Wiggle wires.
May be bad keyboard. If you have another or a friend try a different keyboard.

Check everything else is connected correctly, sometimes issues is not what you think it is. 
I had a bad power supply that had worked on old system but would not work with my then new build. Nothing came on in the way of lights.

---

