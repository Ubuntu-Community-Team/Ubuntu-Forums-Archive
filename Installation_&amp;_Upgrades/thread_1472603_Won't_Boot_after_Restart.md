---
title: "Won't Boot after Restart"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by taprimo on 2010-05-04
I successfully installed 1.4 last night.  ran perfectly.  Asked me to install the NVidia graphics driver.  Not problem, still worked fine.  Had to reboot, no problem worked just fine.  Shut the machine down and two hours later the machine starts, goes through Bios, says booting OS, then restarts.  just stays in this loop.  

I also installed virtualbox, which opened fine when tested.  I did not add a new OS.

I re-inserted the usb drive i did the original install from and it the install program loaded fine.


Is there a way to role back to the last known good configuration?

Trevor


I searched but hope this is not a repeat that I missed.

---

### Post by oldfred on 2010-05-04
Is this before or after the grub menu. If you only have Ubuntu hold down shift key to get menu. 

If before grub menu run this:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

If after grub menu, go into menu and try recovery mode.

---

