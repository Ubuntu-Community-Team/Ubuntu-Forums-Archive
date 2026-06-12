---
title: "PXE Install finishes, but no subsequent booting."
date: 2010-05-05
forum: Installation &amp; Upgrades
---

### Post by jrronimo on 2010-05-05
I have a Toshiba Satellite A55-S106 with a bad CD-ROM. It can't boot to USB, so I've taken to doing PXE installs.

I had done a PXE install for 9.10. After the install, GRUB told me that it couldn't find the UUID. I was able to edit the grub config file and remove references to the UUID and it booted okay.

I tried to do an upgrade from 9.10 to 10.04. The whole upgrade finished, and upon rebooting I saw the purple Ubuntu screen with the red dots, then a blank screen and no hard drive activity. I'm able to read the drive in a LiveCD Environment, but I can't figure out how to make it boot yet.

Fearing for the drive, I put a second hard drive in the laptop and installed 10.04 fresh, again using PXE. Same deal -- install finishes, purple screen, then blank screen and no hard drive activity.

Here's a video of the laptop in action: [http://www.youtube.com/watch?v=T0VgfOA05T0](http://www.youtube.com/watch?v=T0VgfOA05T0) -- the status lights from left to right are "plugged in", "power on", and "hard drive".

I feel like this is probably the same issue as before -- where I should go into GRUB and fix the issue, but I can't figure out how to get into GRUB in 10.04!

Does anyone have any ideas as to what might be going on? I have some data on the first hard drive that I'd like -- not irreplaceable, but it would save me some time if I could get the drive to boot. (I apparently said "yeah, encrypting my home directory sounds like a great idea!!")

Thanks in advance.

---

### Post by jrronimo on 2010-05-07
Could there be some piece of hardware in my laptop that isn't supported anymore? It is fairly old, after all. Or maybe some install flag I can set?

Anyone?

---

