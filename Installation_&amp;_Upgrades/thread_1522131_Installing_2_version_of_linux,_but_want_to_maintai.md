---
title: "Installing 2 version of linux, but want to maintain grub control to first distro"
date: 2010-07-01
forum: Installation &amp; Upgrades
---

### Post by Sir_Sid on 2010-07-01
Hi, I currently have 10.04 installed as my primary OS. I also have windows 7 and Ubuntu 10.10 Alpha installed. I would like to be able to play around with the 10.10 without any risk of damaging my 10.04 install. However, it seems grub2 control was transfered to 10.10. How do I return control to my original distro?

---

### Post by darkod on 2010-07-01
Just boot 10.04 and depending what is the device name of the disk you are booting from, execute:

sudo grub-install /dev/sda (change /dev/sda if you are booting from another disk)

That will install grub2 to /dev/sda and that grub2 will be connected with 10.04 because you did it from within 10.04.

Next time, if you want to keep grub from the first install in charge, just select not to install a bootloader with the second linux install. For ubuntu, you control that by clicking the Advanced button in the last screen of the installer.

For other linux versions it might be different but usually all of them offer not to install a bootloader.

---

### Post by Sir_Sid on 2010-07-01
Got it thanks!

---

