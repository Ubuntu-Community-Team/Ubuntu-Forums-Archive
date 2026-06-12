---
title: "Ubuntu Server - Accessibility options missing from installation menu"
date: 2015-11-05
forum: Installation &amp; Upgrades
---

### Post by info33 on 2015-11-05
Setup:
Installing Ubuntu Server 14.04.3 in uefi mode, dual-booting with manufacturer's windows 8.

Problem:
I'm a beginner.  
I have bad eyesight/poor vision/color blindness.
Accessibility/High Contrast (bright white text, black background) options are not available during uefi-mode installation.

Details:
After a lot of experimentation, here is what I've discovered:
Changing setup (bios) options to enable CSM allows booting from dvd.  If I understand correctly, this is "legacy", non-uefi mode.  To dual-boot with windows 8, which is in uefi mode, I must also install Ubuntu in uefi mode.  That's what I want to do.
If I enable csm (non-uefi), then the initial installer screen provides F-key options at the bottom, one of which is Accessibility, and this menu contains a High Contrast option.  This is exactly what I need.
However, if I disable csm to switch to uefi mode, which then requires that I install from usb rather than dvd, a similar installer menu appears, but without the F-key options at the bottom.  I'm stuck, because as soon as I select Install Ubuntu Server, the awful bright-white-background screens appear, and I cannot continue, because I cannot read them.

Please tell me there is a way around this.  If not, please tell me how I can submit a request to the developers asking if they can either change the design to the normal white text/black background, or add this option as with the csm-mode installer so that I can proceed.

Thank you for any help you can provide.

---

