---
title: "Inspiron 910 with 8 GB SDHC as HDD"
date: 2012-11-04
forum: Installation &amp; Upgrades
---

### Post by deadbeef on 2012-11-04
Hello and thanks in advance.

I was given an Inspiron 910 with dead SSD.  With the SSD removed, I can run live well enough from USB/flash drive.  However, I hate the liability of having the flash drive remain in a port.  If possible, I want to save some money and replace the drive with an SD card running 12.04.

My 4GB flash drive was already used to install 12.04LTS onto the Kingston 8GB SDHC.  Yet, when I power down the laptop, remove the USB/flash drive, and reboot with the SD card inserted, I get "no operating system found" message.  BIOS is set to boot through USB and removable devices only.  Gparted shows the SD card with boot flag, but that's all that I know to look for.

Here it is- Can the SD be used as a replacement for the SSD?  I'm not worried about performance, but want stability and ease of start up.  

Thank you for your simple and productive comments.

**Update

I tried again to install 12.04 onto the SDHC.  This time, I made some changes to the install in the partition settings, and I think I may have stumbled upon the cause of my issue.  Close to the end of the install, I get a bootloader install failure message.  I am then presented with a choice to proceed without bootloader or to install to a different place.  Default recommendation is /dev/mmcblk.  I can select /dev/mmcblk0  SD SD8GB (8.2 GB) or /dev/mmcblk0p1.

Does this help the diagnosis/prognosis?

**update #2

After a sleepless night, I came up with some thoughts.  Must I make the USB/Flash drive "persistent"?  Can the USB/Flash drive be configured to be removed after the system is started if the OS is installed to the SDHC?  Now, when I remove the flash drive, the system crashes, of course.  Is the main problem here in getting the OS to start?

---

