---
title: "Grub Problem in Ubuntu 14.04"
date: 2014-06-19
forum: Installation &amp; Upgrades
---

### Post by campos20 on 2014-06-19
Hi all.

I'm totally clueless here. I installed Ubuntu 14.04 in my notebook (previously with Ubuntu 12.04) using a flash drive. But now, there's a grub prompt saying that "Minimal BASH-like line editing is supported". I can't access bios (actually, UEFI), I can't boot from an usb stick. Whenever I press bios button, the grub prompt shows up before. I also tried to press the boot order button, and I got the same result. I've been reading forums for 2 hours.

Thank you.

---

### Post by grahammechanical on 2014-06-19
You are getting the Grub boot menu. Did you upgrade from 12.04? If you did then you can look under Advanced Options for Ubuntu and you can try booting into an earlier kernel.

If you fresh installed then a re-install might be the easy option. For some reason Grub is unable to load Linux and you are being put at a Grub rescue prompt. Do you get any other information as to why Grub is dropping into rescue?

Regards.

---

### Post by campos20 on 2014-06-19
It was a fresh install. I can't boot from flash. I cant access bios page. Grub prompt simply pops up. It doens't matter if I press, F10 (bios), F9 (boot order), with or without a USB. I tried external DVD reader. Thank you for your quick response!

---

### Post by oldfred on 2014-06-19
Some systems get locked up and you need a full power down or cold reboot. And if laptop remove battery and hold power switch for 10 sec to drain capacitors. 
Then see if quickly before grub starts you can get into UEFI.

What system is this, some have posted various solutions.

---

### Post by campos20 on 2014-06-21
I'm not sure if I should put as "Solved". I opened my notebook, removed the HD. As I could not pass the Grub prompt in my notebook, I put the HD in a PC and used a Live CD in the PC to save data and completely format it. I then put the HD back in the notebook and installed Ubuntu again.

---

### Post by oldfred on 2014-06-21
That also works. :)

---

