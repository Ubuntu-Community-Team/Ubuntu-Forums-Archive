---
title: "Installing from USB and usb wont mount, help.............."
date: 2008-08-01
forum: Installation &amp; Upgrades
---

### Post by bijeeshvs on 2008-08-01
I have installed hardy from a usb thumb drive, every thing works fine but now i cannot mount usb drives when i try to mount a thumb drive it says invalid option , and in gparted it says the mount point is cdrom ( for usb drives )  any solutions????????????????????

---

### Post by bijeeshvs on 2008-08-01
Anybody know how to solve this????????????????????

---

### Post by Rallg on 2008-08-01
If Ubuntu will run, try this:

Make a duplicate of file /etc/fstab, in case this doesn't work and you have to restore it (using the live CD).

Edit /etc/fstab. From Terminal:

gksudo gedit /etc/fstab

Comment out any reference to CDROM or USB. Save the file.

Re-boot. Did that work? If it did work, then you might have a future problem if you ever need to read something from the Ubuntu CD, while operating Ubuntu from the hard drive. That probably won't happen. To reduce the likelihood or future error, open Update manager and remove the Ubuntu CD from its list of archives (if it is there).

If that didn't work... Someone else want to offer advice?

---

