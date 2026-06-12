---
title: "Dual GPU, Triple Head Lucid Issues"
date: 2010-01-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by TheSpecs on 2010-01-21
Hello!

Ok, so here's my dilemma; I have been happily using 2 screens on one GPU for years with Ubuntu. Recently however i decided to buy a new screen and wanted to give 3 screens a go with a second GPU.

Once installing the new graphics card i firstly booted into windows; it detected and installed everything needed. I just enabled it and away i went. Awesome i thought, if it works in Windows it must work in Ubuntu too... i thought.

(Note: I use the nvidia official driver in Ubuntu)

1st Try: 32bit Karmic - Fails to detect the second GPU.
2nd Try: 32bit Lucid - Fails to detect second GPU

I read up on the issue and talk about virtual memory kept coming up, along with needing 64bit, so...
3rd Try: 64 bit Lucid - Success! Well a small one. The nvidia-settings application showed the second GPU and the attached screen to it. 

I Enabled the second screen as a separate X screen, guessed twinview is just that, 2 views. But hey ho, thought it would be a start to see the third screen working. Save the config and reboot to find that although all 3 screens turn on, showing signal, that they are all blank APART from a loading mouse on the main screen. I cannot move this mouse onto the other two screens, nor does it ever stop "loading."

I've Googled the hell outta it and hoping for some insight from any Gurus in the area? Any one have a triple head system working fine?

(If theres any other info you need, please just ask ;))

---

### Post by TheSpecs on 2010-01-27
Hello!

Right no replys yet unfortunately, but im going to add some more information:

On boot this is what happens:
[LIST]
[*]Flashing of all three screens
[*]Nvidia logo flashes on the 3rd screen, attached to the second GPU
[*]Mouse appears which cant be moved and is frozen on the loading mouse, but does not spin.
[*]Flashes more
[*]And... then more frozen mouse
[/LIST]

I have updated the system through the recovery console.

Errors from Xorg:
...
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
...
(EE) ioctl EVIOCGNAME failed: Inappropriate ioctl for device
(II) UnloadModule: "evdev"
(EE) PreInit returned NULL for ""Logitech USB-PS/2 Optical Mouse""
...
(EE) ioctl EVIOCGNAME failed: Inappropriate ioctl for device
(II) UnloadModule: "evdev"
(EE) PreInit returned NULL for ""Macintosh mouse button emulation""
(EE) Jan 25 09:29:05 NVIDIA(0): Error recovery failed.
(EE) NVIDIA(0):  *** Aborting ***
(II) "Power Button": Close
(II) UnloadModule: "evdev"
(II) "Power Button": Close
(II) UnloadModule: "evdev"
(II) "ELAN USB KEYBOARD": Close
(II) UnloadModule: "evdev"
(II) "Logitech USB-PS/2 Optical Mouse": Close
(II) UnloadModule: "evdev"
(II) "cx88 IR (digitalnow DNTV Live! ": Close
(II) UnloadModule: "evdev"
(II) "Macintosh mouse button emulation": Close
(II) UnloadModule: "evdev"
(WW) Jan 25 09:29:06 NVIDIA(0): The NVIDIA X driver has encountered too many errors.  Falling
(WW) Jan 25 09:29:06 NVIDIA(0):     back to write-back cached memory.
(EE) Jan 25 09:29:06 NVIDIA(0): Error recovery failed.
(EE) NVIDIA(0):  *** Aborting ***
(EE) Jan 25 09:29:06 NVIDIA(0): Error recovery failed.
(EE) NVIDIA(0):  *** Aborting ***
(EE) Jan 25 09:29:06 NVIDIA(0): Error recovery failed.
(EE) NVIDIA(0):  *** Aborting ***

Is any of that helpful / related... anyone?

---

