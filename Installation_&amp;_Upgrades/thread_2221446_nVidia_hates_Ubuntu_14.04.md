---
title: "nVidia hates Ubuntu 14.04"
date: 2014-05-02
forum: Installation &amp; Upgrades
---

### Post by age2 on 2014-05-02
Solution to this thread:
[http://ubuntuforums.org/showthread.php?t=1025842&highlight=emachines+hates+linux](http://ubuntuforums.org/showthread.php?t=1025842&highlight=emachines+hates+linux)

Wherein a tiled, distorted screen is displayed after booting an Ubuntu distro occurs, followed by a total freeze, and need to hard reset.

was found here:
[http://askubuntu.com/questions/131125/ubuntu-12-04-64-bit-after-installation-help](http://askubuntu.com/questions/131125/ubuntu-12-04-64-bit-after-installation-help)

From the page:
> You should try adding nomodeset to the default boot again.  After the BIOS screen finishes on your computer press Esc quickly and then scroll to the kernel you want to boot.  Add nomodeset to the end of the line which starts with "linux" and then boot.
 If that works you'll want to make it permanent in which case you have to edit the default grub file:

  sudo gedit /etc/default/grub
  add nomodeset to end of the line which starts with GRUB_CMDLINE_LINUX_DEFAULT then type sudo update-grub and reboot.

If doing multi-boot (as I was with Windows XP), you need to press e when given the option to select which OS to boot, then add nomodeset in the location specified.

However, upon doing this in Xubuntu 14.04 (and even after making it permanent in /etc/default/grub), resolution was fixed to 680x420 (-ish). This was because of Nouveau driver. Had to switch to legacy nVidia driver 314 [-ish] (proprietary, tested) in Additional Drivers.

Thankfully, this worked.

**Edit:** Not just Emachines EL1200-01e (however all Ubuntu variants have this bug on Emachines apparently), also happened on HP Pavilion a6457c. Both PCs use nVidia built-in graphics, therefore, must be conflict with Nouveau (which Ubuntu 14.04 uses as default) and nVidia.

---

