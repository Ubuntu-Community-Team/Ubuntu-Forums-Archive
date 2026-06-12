---
title: "Problems with 14 install on dell xps 9350"
date: 2016-08-31
forum: Installation &amp; Upgrades
---

### Post by eric127 on 2016-08-31
I am trying to dual boot ubuntu 14 and windows 10 on my dell xps 9350. They have both been installed and the windows side boots fine. However when I attempt to boot into ubuntu I get the following error

Error parsing pcc from pcct subspaces
ata3.0: exception Emask 0.0

I made sure fast boot is off on the windows side and secure boot is off. I have already tried reinstalling ubuntu many times but I always get this error when I first boot into it. Any help will be greatly appreciated.

---

### Post by Bucky Ball on 2016-08-31
Are you installing Ubuntu in UEFI mode? That may be your problem. Win10 uses UEFI so Ubuntu needs to be installed in that mode, too. You are possibly installing it in legacy mode. Please confirm.

You also need to switch off hibernation in Win10 before installing Ubuntu.

---

### Post by oldfred on 2016-08-31
Similar Dell models:

I think this has become a mega-thread, may be best to start on last page & work forward. 
 Dell Xps 15 9550  Ubuntu 15.10 on new Infinity display (i7 6gen 16gbr UHD 4k touch) post 272 says 16.04 good
[http://ubuntuforums.org/showthread.php?t=2301071](http://ubuntuforums.org/showthread.php?t=2301071)
[http://ubuntuforums.org/showthread.php?t=2301071&p=13447241#post13447241](http://ubuntuforums.org/showthread.php?t=2301071&p=13447241#post13447241) 
      
 Install Ubuntu 15.10 on Dell XPS 15 2015 9550 with Nvidia 960
[http://askubuntu.com/questions/736613/install-ubuntu-15-10-on-dell-xps-15-2015-9550-with-nvidia-960](http://askubuntu.com/questions/736613/install-ubuntu-15-10-on-dell-xps-15-2015-9550-with-nvidia-960)
Dell XPS 13 9343 Needs /EFI/Boot/Bootx64.efi to boot
[http://askubuntu.com/questions/731931/uefi-not-finding-a-bootable-system-on-xps13](http://askubuntu.com/questions/731931/uefi-not-finding-a-bootable-system-on-xps13)
[https://bugs.launchpad.net/dell-sputnik/+bug/1499323](https://bugs.launchpad.net/dell-sputnik/+bug/1499323)

---

### Post by eric127 on 2016-08-31
I am installing it in Legacy/BIOS mode. However I also had this problem earlier when I was just doing a singular Ubuntu boot on the laptop. Thats why I had to put windows back on it. Wouldn't a singular legacy boot work fine?

---

### Post by Bucky Ball on 2016-08-31
> **eric127 said:**
> I am installing it in Legacy/BIOS mode.

It definitely won't work like that if you have Win10 installed in UEFI. 

> **eric127 said:**
> However I also had this problem earlier when I was just doing a singular Ubuntu boot on the laptop. Thats why I had to put windows back on it. Wouldn't a singular legacy boot work fine?

Yes. It should work fine, but was Win completely removed and you started with a blank disk with a new partition table? Hard to know what the problem was without knowing what problem you were having with the single install.

---

