---
title: "Install stalls on PCG-FX109K"
date: 2010-09-05
forum: Installation &amp; Upgrades
---

### Post by Jamface on 2010-09-05
I'm still trying to run Ubuntu on my Sony Vaio PCG-FX109K laptop. So far I have been trying for 2 years off and on, mostly off. Now I'm trying 10.4 but the problem is the same as before.  After a few seconds I get a blank screen except for the cursor flashing near the top left corner - keyboard is dead, except for Ctrl+Alt=Del goes to reboot.  So I tried the Wubi install. Same result. But the files do seem to be installed in Windows.  So I tried booting 10.4 in recovery mode with various tweaks to the BIOS, e.g. disabled plug and play and power settings. Same result, but the last few lines of the boot so far, before the dreaded cursor appears, are as follows:

[0.066505]  EISA bus registered
[0.066596]  ACPI: bus type pci registered
[0.074870]  PCI: PCI BIOS version 2.10 entry at 0xfd9b0, last bus=1
[0.074941]  PCI: Using configuration type 1 for base access
[0.078200]  bio: create slab <bio-0> at 0

Does this give us any clues as to where the problem may lie?
Are there ways I could alter the boot file(s) to get round the problem?
One of my remaining missions in life is to get Ubuntu running on this machine. I would be very grateful for any help you can give. Thanks. Bill

---

### Post by Jamface on 2010-09-05
I seem to be making some progress.  Using the boot options I set acpi=off.  That removed the blank screen and cursor.  The install went ahead but with a bouncy cursor and bouncy barcode-like flashing across a reduced display (17 by 13 cms in the centre of the screen).
What should I try now?
There are 2 icons on the screen: Examples and Install Ubuntu 10.4 LTS all with the purple background.
Should I go for the Install and try to correct the display size and bouncy cursor later or go back to the boot options and try to sort it from there?
Bill

---

### Post by Jamface on 2010-09-05
I tried the Install, but nothing much happened.  The CD drive whirred for a couple of seconds then nothing.  The screen is still as in my previous post.  The cursor seems stable, but whenever I move it using the pad the barcodes flash across the display area. Left alone, after a while the disc drive whirs again and the screen fades to black.  I can get the display back by pressing any key.
The Examples icon is live and brings up the example windows with occasional flashing barcodes which increase when I move the cursor.
What now?

---

### Post by Jamface on 2010-09-05
I've tried the install button again and the install seems to be going ahead - flashing barcodes and all!

---

### Post by Jamface on 2010-09-05
The installation is all but complete, but throughout the reduced display has been unstable with the picture jumping and the vertical bar codes flashing in time with the HD and CD activity.

What is causing this?  How can I restore the display to normal size and stability when the installation is complete?

Your help would be much appreciated as I really don't know where to start with this one, despite having spent the past hour searching this forum and other Ubuntu help sources. 
Bill

---

