---
title: "Freezes on Install"
date: 2010-07-04
forum: Installation &amp; Upgrades
---

### Post by Elijah on 2010-07-04
Hi, 

I've downloaded two iso's of 10.04, one is the default and the other for the netbook. 

Both freezes at the Install window.. all I see is the install window with nothing on it, it's not loading anything. The cd drive stops spinning and the same blank window appears using the usb install. 

Could be a hardware issue? what can I do here? I'm out of ideas... are there other alternative installers?

---

### Post by davidmohammed on 2010-07-04
have you tried booting with i915.modeset=1 or nomodeset as your grub setting? (Press shift on boot to display the list of kernels - press e and add one of the options immediately before quiet splash)

---

### Post by Elijah on 2010-07-04
Thanks for the quick reply! nomodeset worked :) I got past the empty install window, it seems to be installing now hopefully nothing else happens.. 

I was wondering what this nomodeset is and why it stops the install .. (?)

---

### Post by davidmohammed on 2010-07-04
some graphics cards dont work too well with the "kernel modesetting" that is switched-on by default in lucid. Nomodeset is just a quickway to get around this issue.  Nvidia and ATI graphics cards sometimes are affected.

When you complete your install you will need to fix the problem permanently by editing your /etc/default/grub and adding nomodeset i.e.  GRUB_CMDLINE_LINUX="nomodeset".  Dont forget to run sudo update-grub after making the change.

---

