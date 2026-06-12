---
title: "D2500cc will not boot after install (16.04, 18.04)"
date: 2019-01-15
forum: Installation &amp; Upgrades
---

### Post by archaeometrist on 2019-01-15
I'm pulling my hair on this one.

I have a homebrew Intel D2500CC based system that I use to run radios (softrock and so on) and do band scans.  I originally had 14.04 on it, and it worked fine - I didn't plan on having it connected to the internet so I didn't expect to ever change it.

Changing the software caused headaches (I needed functions that weren't in the original package).  I decided to upgrade (via internet) to 16.04.  That was a minor mistake - I had to re-install the software I use, even though I tried to just replace the 14.04 files upon the (online) upgrade.

I ran it like that for a few days, then Friday I decided I'd upgrade to 18.04 (again online).  BAD mistake.  It would no longer boot properly, and from that point on things got worse.

What happened after Friday - Saturday morning I tried putting a Bluetooth dongle in a USB slot.  It seemed to mess up the system as soon as I plugged it in - suddenly some of the software stopped working.  I pulled it.  Then while shifting cables, the out connector on a USB hub broke loose from the board, and the computer locked up (turned out to have really bad soldering - not worth repairing).

Ubuntu 18.04 would no longer work.  I decided to re-install, including reformatting the hard drive.  After that, it booted once, and then started acting weird when I did updates.  From that point, I could get to the grub2 prompt and try to load Recovery mode, but it would only go so far (lots of text flying by - too fast to read) and then the screen would blank and then the monitor would stop detecting VGA.  I tried nomodeset, and several other things - I found that I could get the boot flash drive to load with nomodeset and no paid software (or something like that), but could not get 18.04 to boot normally.  Then something happened - and the boot flash drive would no longer work.  All attempts fail at the point where it would go to a gui screen.

I tried forcing it (through editing the grub commands) to go directly to a terminal, no luck.  I tried to switch to a terminal - never would work (after the 18.04 upgrade attempt).

The F2 setup screen works fine, the grub screen (and command screen) come up no problem.  I can go so far (even now) with the usb boot disk.  The monitor I have is a homebuilt (for special purposes) small touchscreen, resolution 800x600.  I can (with a headache from the distortion) read when it booted to 1024x768, enough so that I could change the resolution - when Ubuntu was working.  I'm at a loss now as to what is happening... except that it seems to be connected to the video somehow.

When things were halfway working, I pulled a lsmod.  Everything there seemed OK, as far as I could tell (I didn't capture it).

Here's a funny symptom - when I try to get the available video modes, vbeinfo finishes with "EDID version 1.3 No preferred mode available  Adapter 'VGA Video Driver': No info available".

Oh, and this may or may not have something to do with it.  I had to change out the cooling fan - the original had stopped working (temperatures never set off alarms or anything like that).  The new fan works, but after booting and reaching the point where the monitor stops detecting the computer, the fan ramps up in speed until it sounds like a vacuum.  I turn off the computer and quickly reboot (and checked the temperatures) - they all were between 30 degrees and 44 (at the worst).  Something weird there.

Thanks for any help that could get this thing up and running again!

Bob

P.S.  If someone would point me to a list of all the grub commands and what they do (not just a tab list), maybe with the options as well, that would really help in doing diagnosis!  I've searched and only found a very short and limited list (where I found vbeinfo).

---

### Post by archaeometrist on 2019-01-16
Update: Solved, and by accident!  In case someone else has this problem... maybe this will help.
I changed the settings to have the video on the DVI port (DVI - VGA adapter), but forgot to switch the cable over.  The bios settings were for a single active video port - the DVI port only.  The VGA port was not set as a second port.
The LVDS port was also turned off.

I noticed as soon as I powered the computer up, that it showed video from the system, although it was distorted.  I was able to work around that (nomodeset and non-free software disabled did it) and re-install 18.04.  It DID help that I temporarily used one of my big monitors to run everything while I set it up - for some reason the live CD - on - usb wouldn't start up properly until I changed monitors.  Once I got everything installed (and both grub and the gui set to 800x600), then I went back to the original special monitor, and it's been going from there.

Moral of story - try the crazy ideas too, you might just get surprised!  (I'd add that while usually accidents end up meaning more problems, THIS time a mistake actually helped!)

---

