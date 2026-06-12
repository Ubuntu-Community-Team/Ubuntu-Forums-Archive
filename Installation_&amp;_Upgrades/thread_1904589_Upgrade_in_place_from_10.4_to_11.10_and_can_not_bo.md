---
title: "Upgrade in place from 10.4 to 11.10 and can not boot"
date: 2012-01-05
forum: Installation &amp; Upgrades
---

### Post by LinuxFanBoi on 2012-01-05
Background:  I have a Dell Inspiron m5010 that was running Ubuntu 10.4 without issue. I decided to wait until after the fall semester was over to attempt an upgrade because I was taking blah blah blah ++ and didn't wait to screw up my blah blah blah.

So here's what I did.  With my working 10.04 system, I upgraded to 10.10.  It wouldn't boot, so I chose to boot into recovery mode.  From there I upgraded to 11.04...  Again it failed to boot, so again I chose to boot into recovery mode and again I upgraded to 11.10.  Now here I am again with a system that doesn't boot. 

What I have tried so far:  Booting with acpi=off, Booting with noacpi, booting with both acpi=off and noacpi.  I have tried replacing the grub options "quiet splash vt.handoff=7" with "--verbose single," then at the CLI entering "sudo apt-get update," "sudo apt-get install fglrx," and rebooting, but no luck so far.

I need help! no way my system is usable with 10.04 but impossible to run 11.10.  Please tell me what files to provide and I'll do my best to paste them, but without a working system it will be hard.

---

### Post by mastablasta on 2012-01-05
First off i am sure oyu tested the 11.10 in live session before doing the upgrade, right? right?
 
secondly did you use any proprietary drivers before? If so you would have to remove them first before doing the upgrade. this hint (that u used some proprietary drivers) is provided in your attempts in saving the boot.
 
try to boot to cli and remove and purge fglrx (if that's what you were using) and then reboot and that should bring you to GUI where you can install new drivers.
here is how: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch")
 
Check under: Problem: Need to fully remove -fglrx and reinstall -ati from scratch

---

### Post by LinuxFanBoi on 2012-01-05
Yes, I tested it from a USB stick though I did have to add acpi=off to grub to get it to boot.

I tried the instructions you provided and while every command they prescribed seemed to work as intended, I still got no result.  So,  I booted up to command line and using sftp, I backed up my important files to my university account and did a fresh install.

Still I had to use acpi=off from grub, but other than that the install went off without a hitch, even had wifi connected.  but after the install I attempted to log in.  After entering my password, I heard the good old Ubuntu log in music but that's where things fail.  I Just don't know what to do anymore, please help.

---

