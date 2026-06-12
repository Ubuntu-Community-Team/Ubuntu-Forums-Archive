---
title: "No common cd-rom detected Xubuntu 8.04"
date: 2008-07-01
forum: Installation &amp; Upgrades
---

### Post by moonraker77 on 2008-07-01
Hello everyone,

I've run across a problem that many people have similar problems but I have been unable to find any solutions specific to me.

When I attempt to install Xubuntu 8.04 on a single board computer with the following specs:

AMD ElanSC520 133 MHz
64 MB RAM
2 GB CompactFlash via IDE adapter 
Floppy drive
CD-ROM drive via IDE (both CF and CD-ROM are on same IDE)

My goal is to only install the command-line system.  I boot to the CD via SmartBootLoader and it starts the install fine.  After I pick the language and autodetect the keyboard the install is unable to continue stating "no common CD-ROM drive was detected."  I try to manually install it but when I check /dev there isn't any possible drivers.

I have switched CD-ROM's from an LG model to a NEC model and they both are the same.  I have tried all sorts of boot options including hdc=cdrom hdc=noprobe and I've used Expert mode but all roads lead to the same hole.

I'm currently downloading Xubuntu 6.06 to see that works, but in the mean time I would be open to any suggestions.  I've checked the checksums and burned multiple copies, as well as reading just about every thread I can find and googling for solutions.  If anyone can point me at a solution that has actually worked please do.

---

### Post by moonraker77 on 2008-07-02
Apparently this is a known bug...does anyone know what causes the issue in the first place?

---

### Post by moonraker77 on 2008-07-02
I successfully installed Xubuntu 6.06 so it must have something to do with more recent versions.

---

