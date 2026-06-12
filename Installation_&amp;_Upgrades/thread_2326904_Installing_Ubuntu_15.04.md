---
title: "Installing Ubuntu 15.04"
date: 2016-06-05
forum: Installation &amp; Upgrades
---

### Post by Adam_Ehrlich on 2016-06-05
Im trying to install on an HP Notebook 17-p110nr.  

After enabling "Legacy Support" and changing that boot order to "Internal CD/DVD ROM Drive" as initial, I finally got GRUB to pop up.  Then I went through the install and thought everything was good.

Now with Legacy Support still enabled, I changed the initial boot to "Notebook Hard Drive".  When I boot up, I get "Reboot and Select proper Boot device or Insert Boot Media in selected Boot device and press a key".

When I disable Legacy Support and boot up, it says "Boot Device Not Found Please install an operating system on your hard disk."

When I try to run the Live disk, the screen turns black.

Please help.

Thanks,

Adam E

---

### Post by ubfan1 on 2016-06-05
First, 15.04 support has ended, you really should install either of the Long Term Support versions 14.04 or 16.04.  If you machine is UEFI which came with Windows, then the disk partitioning is gpt.  Are you dual booting with Windows?  The install mode should be the same as Windows, UEFI.  If you tried to install grub in legacy mode to a gpt disk, you would have needed to make a grub-bios partition to hold the core.img part of grub.  I think you'd be better off reinstalling 16.04 in UEFI mode, and searching here for the non-UEFI standard things HP does (like requiring specific names for the bootloaders).

---

### Post by Bucky Ball on 2016-06-06
As above. Go for 16.04 LTS. It is a long-term support release, supported until 2021.

---

