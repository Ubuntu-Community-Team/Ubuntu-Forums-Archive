---
title: "Ubuntu 10.04 install - Screen goes blank and music plays"
date: 2010-08-14
forum: Installation &amp; Upgrades
---

### Post by AceGambit on 2010-08-14
I have a machine that is "dual-booted" for Windows XP and Ubuntu 10.04.  This was done using wubi.  Something happened and the Ubuntu section wouldnt boot anymore.  This is the third time this has happened to me with wubi so I decided i was just going to format the drive and make it 100% ubuntu boot.

It's an AMD64 machine so I downloaded the 64bit ubuntu 10.04 put the disc in the drive and it wouldn't boot to it.  Frustrated I put the image on a usb stick using unetbootin (windows).  I put the stick in, and it boots.  I get the purple screen with "Ubuntu" and the dots as the OS Installer loads.  Then the screen goes blank and my monitor shows "no input".  The speakers then play the Ubuntu welcome sound.  And it hangs from there.  

Here's what I've tried:

Disabled Floppy drive in BIOS

Pressed F6 and loading screen (was presented with a bunch of text that didnt mean much to me. "cannot open \dev\sr0: no medium found" Was displayed about 8 times.

Immediately after the loading screen went away (before the sound played) I pressed and released the power button the the PC.  I was presented with a screen (that looked a lot like the F6 one) that had some I/O Error message repeated from top to bottom.

Any help would be greatly appreciated.  I've resolved that it is probably a graphics card problem, but am not sure about the work-around. Graphics card is onboard Intel 82915G/GV/910GL Express Chipset.  processor Pentium 4 2.80 GHz.  1G Ram.

Thanks,

Kurt

---

### Post by MAFoElffen on 2010-08-14
What's your hardware... especially graphics?

---

### Post by AceGambit on 2010-08-14
> **AceGambit said:**
> Graphics card is onboard Intel 82915G/GV/910GL Express Chipset.  processor Pentium 4 2.80 GHz.  1G Ram.

The Machine is an IBM Think Machine Desktop.  It's got a DVD Rom Drive and a Floppy Drive.

---

### Post by MAFoElffen on 2010-08-14
>  I was presented with a screen (that looked a lot like the F6 one) that had some I/O Error message repeated from top to bottom.
--> Was there a message noting CPU corruption on that "screen"?
...And can you access the drive from XP?  Can you run from a LiveCD?  And what kind of Graphics on that?

---

### Post by AceGambit on 2010-08-14
The screen is black with white text:

```
(process:259): GLib-WARNING **: getpwuid_r(): failed due to unknown user id(0)
		*setting sensors limits				[OK]
*Speech-dispatcher configured for usuer sessions
		* Starting Common unix Printing System; cuspd	[OK]

cpid: exiting

init: rc main process (1734) killed by TERM signal
init: tty4 main process (1735) killed by TERM signal
init: tty5 main process (1739) killed by TERM signal
init: tty2 main process (1753) killed by TERM signal
init: tty3 main process (1756) killed by TERM signal
init: tty6 main process (1761) killed by TERM signal
init: cron main process (1772) killed by TERM signal
Checking for running unattended-upgradesL init: avahi-demon main process (1224) terminated with status 255
modem-manager: Caught signal 15 shutting down...
init: disconnected from system bus
...
...
...
mount / is busy
*casper is resynching snapshots and caching reboot files

```

(not the same text i got last time)

Havent tried a Live CD yet, but I'll download one and try.

---

### Post by AceGambit on 2010-08-14
I got the IO error again:

```

[  31.XXXXXX] end_request: I/O error, dev sdb, sector 518XXX

```
Where X = a different number on each line

---

### Post by MAFoElffen on 2010-08-14
Is it an IBM Think Centre with an onboard Intel 82865G Extreme 2 graphics?  With or without the AGP add-in card?  It should be OpenGL and  Vesa compatible, so there is something you can try to boot it... if that's what you have.

---

### Post by AceGambit on 2010-08-14
Yeah it IS an IBM Think Center (Centre) withOUT AGP.  I have two PCI slots and a PCI Express slot.  All are empty.  Im using the onboard integrated Intel Graphics.
This is all I know about the graphics device (from Windows XP device manager)
Intel 82915G/GV/910GL Express Chipset.

---

### Post by MAFoElffen on 2010-08-14
Try this:  While booting to Ubuntu, hold down the "Shift" key.  It should bring up the Grub Menu.

Press "e" on the first menu line. Go down to the line that resembles:
  ```
 terminal and then open that file from your removable  drive...

linux     /boot/vmlinuz-2.6.32-24-generic  root=UUID=32939def-1f4a-4134-9b56-bed2319a9216 ro   [COLOR=Red]quiet splash[/COLOR]
```edit  it to remove "quiet splash" and type in it's place "i915.mode=1".  Press Control-X to boot.

You might also try "i915.mode=0", "xforcevesa" or "nomodeset"... which I've heard people running with all four of those options with that chipset.

If it works, I'll tell you "what" to change "where," to make it  permanent in GRUB.

...If for some reason you can't get to a grub menu, tell me and I'll tell you how to change it in what file.

---

### Post by AceGambit on 2010-08-14
Hey, 

sorry it took me so long to respond, I only had one USB stick and i was trying different ISOs to see if any would work.  So i had to re-format and go back to the one i was using before (i like to keep things consistent)

I tried holding shift just as the computer booted.  it took me into the unetbootin bootloader (i think) anyway, i found my way to the boot options commands and replaced "quiet splash" with what you said.  

It booted into live desktop!  I'm running the GUI installer now.  Will let you know how it turns out.

THANKS SO MUCH!

---

### Post by AceGambit on 2010-08-14
Alright, Install went well, on reboot, i got the same results, so i held shift and It was nice enough to let me into GRUB.  where i made the same change again.  I've made permanent changes to GRUB in the past i just don't remember where (or how).

---

### Post by MAFoElffen on 2010-08-14
Great!  Good Luck. Please mark your thread "solved."

---

