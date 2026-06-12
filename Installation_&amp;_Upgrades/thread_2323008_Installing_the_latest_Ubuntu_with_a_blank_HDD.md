---
title: "Installing the latest Ubuntu with a blank HDD"
date: 2016-05-02
forum: Installation &amp; Upgrades
---

### Post by doublea2 on 2016-05-02
I seem to be having some issues with installing the latest Ubuntu with a blank 1TB HDD.  I go through the normal process & I am currently on the Ubuntu test before install mode, now when I try to install Ubuntu I get to the Installation Type area, it shows nothing..  I'm including two screen shots, one of the installation type issue and one with what I have setup in Gparted. I am quite new to installing Linux Distributions and have no real clue as to where to proceed so any help would be greatly appreciated! :)  **Gparted** [https://dl.dropboxusercontent.com/u/69039014/Screenshot%20from%202016-05-02%2011-08-33.png](https://dl.dropboxusercontent.com/u/69039014/Screenshot%20from%202016-05-02%2011-08-33.png)  **Installation** **Type** [https://dl.dropboxusercontent.com/u/69039014/Screenshot%20from%202016-05-02%2011-07-46.png](https://dl.dropboxusercontent.com/u/69039014/Screenshot%20from%202016-05-02%2011-07-46.png)  Also, when I do not have Gparted open I do see both of the partitions on the Ubuntu sidebar..  Ps. I am trying to install Ubuntu to the HDD, not a USB.

---

### Post by sudodus on 2016-05-02
Welcome to the Ubuntu Forums :-)

Something is wrong. You say it is a 1 TB HDD, but the information in gparted indicates that it is a 2 TB HDD. Which is correct?

I assume that you have nothing of value installed in the system. If the current system is somehow bad, I suggest that you try to get a clean partition table.

***A. First try***

1. Create a new partition table with ***gparted***. (It will remove all current partitions, file systems and files.)

2. Start the ***installer*** and install Ubuntu to the whole drive. This is the easiest way to do it.

***B. Next try***

If this does not work, it is probably because there is some old data in the drive, that makes the installer confused.

1. Then I suggest that you use ***mkusb*** to wipe the first megabyte and install a fresh partition table and file system. See these links

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

[mkusb/wipe](https://help.ubuntu.com/community/mkusb/wipe)

2. Start the installer and install Ubuntu to the whole drive.

***C. More advanced***

1. You can create a partition table with ***gparted*** before installing Ubuntu. Maybe you want a big **data** partition, and install Ubuntu to a small part of the drive, maybe 50 GB for the root partition and make a swap partition of 5 GB. Maybe you want partitions for other operating systems.

2. Start the installer, and at the partitioning window, select **Something else** and select the partitions where you have intended to install Ubuntu's root partition and swap partition.

D. You may or may not need/want to discuss UEFI and GUID partition table, GPT. Is there another operating system in another drive (in the same computer)?

See this link: [Installation/FromUSBStick#UEFI](https://help.ubuntu.com/community/Installation/FromUSBStick#UEFI)

---

### Post by doublea2 on 2016-05-02
@sudodus

Thank you for the quick reply but I actually managed to wipe the drive one last time using a usb-boot to gparted, then tried again and was able to to a complete install :D

I also just noticed that my text in the first post apparently got jambaled and looks really bad..
Sorry about that.

---

### Post by sudodus on 2016-05-02
Thanks for sharing your solution and marking this thread as SOLVED :KS

---

