---
title: "How Can I Install Linux on an SD Card?"
date: 2015-08-03
forum: Installation &amp; Upgrades
---

### Post by ChannelZ28 on 2015-08-03
I have a Dell Mini laptop with an 8gb SSD. I also have a 32gb class 10  SD card. Since 8gb isn't enough to run an OS, I want to run it off the  SD card. I can't remember how to do it. Someone already told me how in  this forum, but it was a while ago and I can't find the post. Could  someone could give me a fairly detailed description of how to do it? I  want to use Elementary OS Freya, but instructions for Ubuntu or Lubuntu  would be fine. I assume they are pretty much the same. Thanks!

---

### Post by yancek on 2015-08-03
The installation procedure is the same.  You will have to determine how the SD card is seen.  Linux drives show as sda, sdb, etc.  You should be able to determine which one it is because you know the size.  Use fdisk -l or use GParted to show drive/partition information.

---

### Post by efflandt on 2015-08-04
If you make bootable USB memory with the live/install iso, boot to a live system, open a terminal window (typically Ctrl+Alt+T in Ubuntu), insert an SD card, and see what tail end of dmesg command shows for it. If it shows it as usb mass storage then you should be able to boot from it. If it shows as some other type of block device you typically cannot boot from it. In laptops the SD card slot is usually the other type of (unbootable) block device. In my Acer P500W tablet PC (netbook size with detachable keyboard) 2 GB RAM, Win7 Pro on 32 GB SSD, the SD slot is internally USB connected, so I am able to boot from that. I have both Ubuntu 12.04 and Lubuntu 12.04 sharing common /home partition on 32 GB SD, 3 partitions total (no swap), to try both some time ago, but only installed grub from Ubuntu. Worst case if your SD slot is not USB, you may need a USB card reader.

Also from the live system run **sudo fdisk -l** (small L) to see which device is which. When you boot the live system from USB it may be seen as /dev/sdb and the SD card as /dev/sdc. But once installed it will likely boot as /dev/sdb. That should not be a problem because grub uses UUID to identify partitions, not the /dev/.

It would be best to put grub on the device where you install Linux, and to assure that you should select **Other** when it comes to the partitioning part of install, figure out your own partitions, and make sure grub is put on the same device Linux is being installed on (drop down list at bottom of screen?). Grub should go on the device without a number to put it in the mbr (like /dev/sdc, NOT dev/sdc1).

To boot Linux after installed to SD, press the hotkey during the BIOS splash screen to select the boot device (typically F12 for Dell) and boot the SD card.

This all assumes that your Dell Mini came with Win7 or older which uses BIOS, not UEFI (Win8+).

---

### Post by Bucky Ball on 2015-08-04
Use [UNetbootin]("http://unetbootin.github.io/"). That's it. As mentioned, the procedure is exactly the same as creating a Ubuntu install USB. :)

---

### Post by QIII on 2015-08-04
Bear in mind that SD cards are painfully slow, so don't expect screaming performance.

---

