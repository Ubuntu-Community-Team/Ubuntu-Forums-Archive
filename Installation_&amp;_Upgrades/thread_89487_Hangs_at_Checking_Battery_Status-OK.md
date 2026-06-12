---
title: "Hangs at Checking Battery Status-OK"
date: 2005-11-12
forum: Installation &amp; Upgrades
---

### Post by sadalmelik57 on 2005-11-12
I am attempting to boot to the LIVE CD version of Ubuntu 5.10.  My system is a Dell P4 300ghz with 512 mb RAM and ATI 9800 Video Card.

During the boot process the screen goes blank; the monitor buttons indicate no incoming signal, such as when it is in "sleep" mode.  Moving the mouse and keyboard have no effect.  I touch the power button briefly and the monitor turns back on.  The last entry shows "Checking Battery Status - OK."  In a moment the CD ejects from the DVDR/CDRW drive.  The monitor stays on indefinitely.  Leaving the CD out or pushing it back in has no effect.  None of the keys have any effect.  All I can do is reboot, and get back to the same spot.  Any suggestions?

---

### Post by Lambert on 2005-11-12
When you are booting the system and at the prompt

boot:

type this line in

acpi=off

You can also hit F1 for other options to see if anything else might help.

---

### Post by sadalmelik57 on 2005-11-13
I tried the acpi=off command, as well as aic7xxx=no_probe and noapic nolapic, all with no positive effects.

I started in live-expert mode and played until I determined that everything was fine up until the video settings.  I narrowed it down to the screen that supplies multiple uptions for screen size.  The last three options (starting with 640X480) are checked.  I found that by checking a few more options I was able to boot up and see the desktop.

However, the screen resolution is stuck at 640X350 @ 70Hz.  When screens are opened I can't get to the bottom or top of the window to click buttons or choose options.  I can't reset the resolution or screen size.
:confused:

---

