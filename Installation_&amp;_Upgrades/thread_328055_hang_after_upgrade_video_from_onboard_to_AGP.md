---
title: "hang after upgrade video from onboard to AGP"
date: 2006-12-30
forum: Installation &amp; Upgrades
---

### Post by widjajayd on 2006-12-30
I got P4I45GV motherboard and additional  Nvidia 5200 AGP card, P4I45GV has a built-in video. Im having problem istalling Ubuntu 6.10 since Im new in ubuntu and never tried any Linux, can somebody help me what to do? When I change my primary video in BIOS to the built-in, the installation is good, but when I change it to AGP Nvidia 5200 FX, the installation just hangs. Is there any way I could do this right?

I can not use safemode since after booting it hang 
last line iseip is at clear_local_apic+0x21/0xC0

:confused:

---

### Post by dcstar on 2006-12-30
> **widjajayd said:**
> I got P4I45GV motherboard and additional  Nvidia 5200 AGP card, P4I45GV has a built-in video. Im having problem istalling Ubuntu 6.10 since Im new in ubuntu and never tried any Linux, can somebody help me what to do? When I change my primary video in BIOS to the built-in, the installation is good, but when I change it to AGP Nvidia 5200 FX, the installation just hangs. Is there any way I could do this right?

I can not use safemode since after booting it hang 
last line iseip is at clear_local_apic+0x21/0xC0

:confused:

You might want to just do the install with the built-in card, and then you can later change your /etc/X11/xorg.conf file to use the VESA driver and then try the other video card.

If that works, then you can try to get the correct driver installed and working (there may be specific instructions for this in the forum, do a search for them).

---

