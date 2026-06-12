---
title: "FINALLY! Able to install 6.10 on my laptop ATI video"
date: 2006-11-22
forum: Installation &amp; Upgrades
---

### Post by lmmtorres on 2006-11-22
It took me about three weeks of trial and error but I finally got the right settings to run 6.10 on my laptop:

MicronPC TransPort X3100
ATI X700 video card
Sata 2 HDD

Steps:
Boot with the 6.10 CD choose the safe video mode and added the following boot options: vga=791 acpi=off. The laptop boots to a black screen, switched to another console (CTRL-ATL-F3) . Edited the /etc/X11/xorg.conf, changed the ati driver to vesa. Returned to the original console (CTRL-ATL-F7).Restarted the X session (CTRL-ATL-BACKSPACE). Performed a normal installation. Rebooted. Works! For better video performance install the ATI driver ([www.ati.com](www.ati.com)) ver 8.31.5, previous versions did not worked for me. Follow the driver installation instructions.

Good luck!

---

### Post by Koziasty on 2006-11-24
Hm.. I am running an Aspire laptop with ATI x700. As far as I recall, I did have some problem with runing the first option on the boot cd. 
Yet, I didn't mess up with xorg, I simply went for the safe graphics mode... Makes life much easier :)

Regards, Koziasty

---

### Post by wpshooter on 2006-11-24
> **lmmtorres said:**
> It took me about three weeks of trial and error but I finally got the right settings to run 6.10 on my laptop:

MicronPC TransPort X3100
ATI X700 video card
Sata 2 HDD

Steps:
Boot with the 6.10 CD choose the safe video mode and added the following boot options: vga=791 acpi=off. The laptop boots to a black screen, switched to another console (CTRL-ATL-F3) . Edited the /etc/X11/xorg.conf, changed the ati driver to vesa. Returned to the original console (CTRL-ATL-F7).Restarted the X session (CTRL-ATL-BACKSPACE). Performed a normal installation. Rebooted. Works! For better video performance install the ATI driver ([www.ati.com](www.ati.com)) ver 8.31.5, previous versions did not worked for me. Follow the driver installation instructions.

Good luck!

This tells me that this O/S still has a good way to go before it is ready for use by the general public !!!

---

