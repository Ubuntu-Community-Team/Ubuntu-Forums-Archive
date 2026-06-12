---
title: "Can't get install started, infinite loop on blue power-on screen"
date: 2013-03-01
forum: Installation &amp; Upgrades
---

### Post by chavodel8 on 2013-03-01
My apologies if this is a repeat, but the only posts I can find seem to relate to problems once the Ubuntu splash screen is reached. I can't get that far.

I have Windows 7. I want to dual boot. I have a verified, good ISO of Ubuntu 12.4.2 64-bit on CD. I have installed it successfully in a VirtualBox VM on Win7 to ensure the ISO is a good copy.

When I put the ISO CD in the drive and reboot, I see the following steps:
* Blue power-on screen (with F9-Setup, F10-..., F12-Network on the bottom)
* Blank screen
* Purple Ubuntu screen with a keyboard looking icon and a person in a circle icon at the bottom
* I hit any key (usually space or enter) and get a Ubuntu menu, but first a language selection. I choose English.
* I choose either Install Ubuntu or ... I forget the exact text, but the one that means "run Ubuntu off the CD"
* It seems to try to start working on that because once I select one, I can no longer cycle between the options
* After 2 to 5 seconds, the screen goes black
* Here I enter a loop:
** Blue power-on screen shows up again
** Screen goes black

I can take the CD out and Windows won't boot either. I have to do a hard shut down by pushing the power button on the tower. I can then turn it on and boot back into Windows.

Notes:
* If I don't do anything on the first purple Ubuntu screen (the one with the keyboard and person in a circle at the bottom), it will still push into this same loop within 10 to 15 seconds or so.
* This is a corporate machine, so it is possible that IT has put some stuff in place that I know nothing about to prevent dual boots, live CD boots, or wiping and replacing the OS, etc.
EDIT: * My machine is an HP Z600 and has a RAID set up

Any ideas on this one?

Thank you much!

---

### Post by oldfred on 2013-03-01
Desktop installer does not have RAID drivers. Only server and alternative. But alternative is discontinued with 12.10.

 Elimination of Alternative installer for 12.10 and no RAID support directly for Desktop.
[http://ubuntuforums.org/showthread.php?t=2049021](http://ubuntuforums.org/showthread.php?t=2049021)

Do you have permission to install on your machine from corporate?

An external drive or flash drive may be alternatives?

 HOW TO Avoid Wubi & Install Ubuntu on USB Drive -
[http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)

 Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

---

### Post by bcbc on 2013-03-01
Use 'nomodeset'. If you have an nvidia or radeon card then this is likely the issue:

[http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it]("http://askubuntu.com/q/162075/14916")

PS don't get in the habit of hard shutdowns. With linux it's usually unnecessary due to: [http://en.wikipedia.org/wiki/Magic_SysRq_key#Uses](http://en.wikipedia.org/wiki/Magic_SysRq_key#Uses)

In short, hold down Alt+SysRq then press (waiting a couple of seconds before each) R-E-I-S-U-B
(if it's a live CD it's not a big problem because no damage will occur, you can just use Alt+SysRq B (reboot), but if you do this on a real linux install it's possible to corrupt the drive if it's doing writes at that time).

---

### Post by chavodel8 on 2013-03-01
That first link did it for me, thank you! I had to use acpi=off, nolapic, and nomodeset and I had to set them all very quickly, then do the boot, but I was able to do it! Thank you!

---

### Post by bcbc on 2013-03-01
Yikes, acpi=off is a sledgehammer solution that disables a lot of useful stuff. Hopefully you don't really need that. What computer brand/model/graphics card do you have?

---

