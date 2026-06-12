---
title: "Help with Trusty Tahr?"
date: 2014-10-01
forum: Installation &amp; Upgrades
---

### Post by felix16 on 2014-10-01
Hello guys n gals ive been trying to install Ubuntu and keep running into the same problem. I have it installed on a USB and every time i boot into it, i get the ubuntu menu. From here i select install Ubuntu (ive selected try but same problem), and i get a bit passed the grey screen with an flashing underscore. After the screen says "NO SIGNAL" for a few seconds, then the no signal dissapears and it looks as if something is about to pop up on screen, only nothing does. After approximately ten seconds the "NO SIGNAL" sign from my monitor pops back up ive waited it out before and waited 15 minutes waiting before pulling the cord out of frustration. Currently running 64 bit Windows 7 Ultimate with intention of dual booting 64 bit Ubuntu 14.04.1 LTS. Ill include my specs just incase anyone may need it, yes i know my computers a crapwagon but ive seen Ubuntu running on worse ones. Thanks for all the help :p
 [ATTACH=CONFIG]256891[/ATTACH]

---

### Post by JKyleOKC on 2014-10-01
Do you actually have two video adapters, or is the Nvidia just the chip that's in the SiS card? My experience with SiS cards in the past has been that they tend to be difficult to set up properly in any flavor of Linux. You might try selecting "try" and then pressing either shift key immediately and holding it. On a permanent installation this should bring up a Grub menu but I don't know if it will do so from the Live CD/USB. If this does bring up a Grub menu, hit the "e" key to edit the default selection. Then scroll down the resulting display to find the line that includes "quiet splash", use the arrow keys to get to the "q" of "quiet", and insert "nomodeset " (being sure to include the space to separate it from the "q"). Then use CTRL-X to resume the boot process.

This will disable a kernel feature that's been known to create the kind of problem you're having. If it works and lets you use the program, you can install it on your disk from within the "try" option, and then make the modification permanent once you have the system on your disk (by doing the same thing, the first time, and editing the /etc/default/grub file to add the "nomodeset" option for all future boot actions). We can give you detailed directions for doing this, if this suggestion works at all...

---

### Post by Bucky Ball on 2014-10-01
Try this. When at the options menu with 'Try' 'Install' etc. hit F6 and choose the option 'nomodeset'. Proceed. Any different?

Ubuntu should run okay on that set up, but I'd probably go for something lighter myself, Xubuntu perhaps, but that is not the issue here. Changing flavours wouldn't make a lot of difference to the issue you're having I'm guessing.

---

### Post by grahammechanical on 2014-10-02
Pictures to look at. See, section 6 - F6

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Regards.

---

### Post by Bucky Ball on 2014-10-02
Thanks gm. And specifically, from that link, the attached pic is what you get when you hit F6. Choose 'nomodeset'.

---

