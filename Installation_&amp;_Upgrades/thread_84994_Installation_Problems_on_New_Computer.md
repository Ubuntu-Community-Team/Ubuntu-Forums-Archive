---
title: "Installation Problems on New Computer"
date: 2005-11-01
forum: Installation &amp; Upgrades
---

### Post by millet5 on 2005-11-01
Hello everyone,

I just recently purchased a sony VAIO desktop with an Intel Pentium D processor.  When trying to install the Breezy Badger, I get all the way through the first part of the installation, and recieve a message that Ubuntu will reboot my computer and install more packages.  When rebooting, Ubuntu hangs.  Problem is, so much garbage is spilled out that I can't make out what the original problem was.  I tried running with noapic option, or whatever it is suggested for hardware hangups, and the results were the same.  Any help would be greatly appreciated.

---

### Post by az on 2005-11-01
Do you get a login prompt or the thing hangs?

If that is the case, you may just have a misconfigured graphics card.  It is quite easy to fix (and then send in a bug report)

If it truly hangs, what is the last message displayed?

Also, if you do not see the grub menu, hit escape before it boots and chose the recovery mode option.  See if that drops you to a shell (a command line prompt)....

---

### Post by millet5 on 2005-11-01
I never get to the command prompt.. 
the last message that is displayed says something along the lines of generic hardware device driver loaded.
Before that message, there is a lot of jargon that seems to start with something along the lines of 

CPU:0

---

### Post by millet5 on 2005-11-01
Okay, rebooted in recovery mode, and still did not make it to a command prompt, but this time I saw the entire last message...

[4294699.79300] snd-hda-intel: can't be loaded
missing kernel or user mode driver snd-hda-intel
shpchp:already loaded
shpchp:already loaded
uhci-hcd:already loaded
uhci-hcd:already loaded
uhci-hcd:already loaded
uhci-hcd:already loaded
ehci-hcd:already loaded
<6>hw_random_hardware driver 1.0.0 loaded
hw_random:loaded sucessfully

---

