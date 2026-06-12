---
title: "Installation freezes on splash screen"
date: 2015-11-06
forum: Installation &amp; Upgrades
---

### Post by james180 on 2015-11-06
Hi
I'm trying to install Ubuntu 14.04.3 on my HP Envy with an intel i7-5500U processor but the installation freezes at the Ubuntu splash screen with the white and orange dots. 
I've tried with both a DVD and a USB and neither are working. I saw somewhere that it may be due to my graphics card, a Nvidia GeForce GTX 850M, and I had to add the command neuveau.modeset=0 before running installation, but this has not worked out for me either. Could anyone shed some light as to how I may fix my problem?

Cheers, James

---

### Post by Bashing-om on 2015-11-06
james180; Hi !


You did verify the .iso md5sum, and you did verify the burn ? 

In the liveDVD:
Try to boot in "try ubuntu" mode with the boot parameter ' nomodeset ' rather than " neuveau.modeset=0".
We do want to boot the "try ubuntu" and have it work prior to attempting the actual install - in your case .
This parameter 'nomodeset' disables Kernel Mode Setting thus the system will use the fall back driver to boot . Once booted up one can install a proper driver . Either in the live environment ( one time use thing, as any changes will not persist ) or in the install.

In the live environment one gains access to the boot options menu:
as soon as the bios screen clears depress and hold a shift key -> language screen, escape key to accept the default ->
boot options screen -> F6 key for a pop up of boot options.

In the install one edits the boot parameters from the grub menu -> 'e' key for edit mode -> boot parameters screen
in the line starting with linux replace "quiet splash' with nomodeset ; key combo ctl+x to continue the boot process.
Once in the GUI .. Additional Drivers utility to find and install the proper driver.

[INDENT][INDENT]hey, it could happen
[/INDENT][/INDENT]

---

