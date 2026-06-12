---
title: "Can't boot ubuntu after dual boot installation"
date: 2012-06-04
forum: Installation &amp; Upgrades
---

### Post by Lucnarr on 2012-06-04
Hi Everyone,

I'm having issues installing Ubuntu on my PC. I have created a 64 bit 12.4 LTS installation pen drive. I'm attempting to install Ubuntu along with my current Windows 7 setup. This usually works without any issues but this time I'm having problems booting Ubuntu after the installation is completed.

What I initially did was boot the pen drive, re-size my current windows partition and create a 60GB ext 4 partition for Ubuntu.

The installation went smoothly and without error, however, when I tried to reboot after the installation Grub didn't kick in and my PC booted straight into Windows. I've tried doing a re-install 3 times, the third time I deleted the whole 60GB ext4 partition but all with the same result.

I also tried to run the grub-install from the live Ubuntu i booted from the USB but that didn't seem to help either.

Any suggestions?

---

### Post by nj_peeps on 2012-06-04
Make sure you are installing grub to the MBR.  Also, boot using your pen drive, and try grub-update, and watch the output to make sure it is detecting your new ubuntu install.

---

### Post by wilee-nilee on 2012-06-04
Try the boot-repair app, the recommended repair if you are still having problems post the HTTP address of the bootinfo summary generated when you use the tool.

  	 	 	 	 	 	   [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

