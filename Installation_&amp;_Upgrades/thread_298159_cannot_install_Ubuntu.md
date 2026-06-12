---
title: "cannot install Ubuntu"
date: 2006-11-12
forum: Installation &amp; Upgrades
---

### Post by gian on 2006-11-12
Hi,

I'm installing Ubuntu Dapper Drake on a SATA disk inside an Acer Altos G320.

Install fails because of SATA and ATI issues.

About ATI, standard install will fail because the card is not recognized.
If I choose SAFE graphics install will work.

However, at system reboot after install, I get a "no bootable device" error.

If I boot off the install CD and choose boot from first HD, the video flickers and is unusable because of the video driver.

I tried to boot without Xserver using "init 3" or "failsafe" command option, but it doesn't work and I'm stuck...

Please, throw me a lifesaver... <gurgle>

-Gian

---

### Post by wpshooter on 2006-11-12
Does this computer have any other O/S on it - windows, etc. ?

---

### Post by gian on 2006-11-13
no, I only have Ubuntu.

I solved the video issue downgrading the number of colors to 16.
This way I could go on and was able to fix the boot issue.
However, in the device list the video card is still Unknown.

---

