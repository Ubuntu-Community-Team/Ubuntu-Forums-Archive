---
title: "No boot menu at startup after Ubuntu 16.04 install.  boots directly to windows"
date: 2016-05-01
forum: Installation &amp; Upgrades
---

### Post by Chester Labb on 2016-05-01
I have win7 professional installed.  Two SSDs, one with windows installed the second with ubuntu.  Install appears to work correctly until I reboot.  The windows ssd is the boot disk.  Microsoft created a second reserved partition of 100mb at the low addresses  when win7 was installed.  Any suggestions?

---

### Post by yancek on 2016-05-01
Which installation option did you choose?  Where did you install the Ubuntu Grub bootloader, to the MBR of the device or the Ubuntu partition?  You should have installed to the MBR of the SSD on which you have Ubuntu and then set it to first boot priority in the BIOS.  If you can boot Ubuntu, run:  sudo update-grub and it should detect windows and you will be able to select either to boot.  Trying to get windows to boot any Linux is not a simple process.

---

