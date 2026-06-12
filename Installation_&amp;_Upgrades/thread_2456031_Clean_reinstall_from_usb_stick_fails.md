---
title: "Clean reinstall from usb stick fails"
date: 2021-01-02
forum: Installation &amp; Upgrades
---

### Post by wmrp on 2021-01-02
Our Toshiba satellite laptop runs on Ubuntu 20.04 and is stuck on airplane mode so it cannot get on wifi. We have used it on ethernet, so it was not an issue, but now it needs to be using wifi at a different residence. 
 I decided to do a clean reinstall from the same usb stick that I used for the original install (and subsequently for two other computers). Hitting F12 brought up the option to boot the usb, but it failed to proceed from there. Every attempt after that brings up a long bios process before it starts up the currently installed Ubuntu 20.04. Hitting F1 and F2 has the same result.

---

### Post by guiverc on 2021-01-02
I would assume from your description either the ISO was bad (did you validate it? [https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0](https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0)) or what occurs far more regularly in my experience, the write to your install media was faulty. 

If media fails to boot for me (using the last bad write, 5-7 days ago), I tried booting it firstly on another box of the same type (BIOS or uEFI); it failed there, then I tried booting as what I consider an optional step (to prove bad write) booting it on the opposite type of box (uEFI or BIOS). As the media failed to boot on 3 boxes (two of same type with regards booting process), I knew media was faulty.

Re-wrote ISO to media & it booted as expected.  USB flash drives are built for price, nor quality/reliability; bad writes do occur.

---

### Post by GhX6GZMB on 2021-01-02
The story about bad .ISO images keeps popping up, but I've never experienced it myself. Never. IMO, It's a red herring.
File transfers are so well controlled using CRCs, and other error checking/correcting methods that the likelyhood tends towards zero.
Downloading .ISO images from dubious sources is a much bigger problem.

The really big issue where most installs fail is BIOS/UEFI setup. The USB drive MUST be first in the boot sequence. And all other "optimizing" boot options should be turned off.

---

### Post by grahammechanical on 2021-01-02
I am assuming that airplane mode disables the WiFi electronics on the motherboard. A re-install might not change anything if the WiFi adapter is turned off in the BIOS/UEFI settings utility. Is that machine dual booting with Microsoft Windows? If WiFi is switched off in Windows then it does not get switched back on when Ubuntu is loaded.

What output do you get from this command?

```
rfkill list
```

If the readout is yes to Hard blocked then the WiFi electronics are physically switched off.

Regards

---

