---
title: "Installer does not see Windows Installation"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by bangbang023 on 2010-05-03
I have three physical drives:

Drive 0: Used for paging file in windows and general temp file storage
Drive 1: Media storage
Drive 2: Windows installation

When booting off the Ubuntu 10.04 disc and running the installer, it gets up to the partition step and doesn't find my Windows installation (for the automatic partitioning and such) and lists Drive 0 as the drive it will install to. I really want it to see my Windows install and create a partition on that same drive. Can anyone help me in getting the installer to see the Windows installation?

---

### Post by frantid on 2010-05-03
select the manual partitioning option, that way you can control it how you want.

---

### Post by bangbang023 on 2010-05-03
I did that (after shrinking the Windows partition from within Windows), but then it booted straight into Windows after install. I'm assuming, after that, I would have to use something like EasyBCD to edit the windows boot loader to add the option to load Windows or Grub, but I'd like to avoid editing it myself, if I can.

---

### Post by frantid on 2010-05-03
no something is wrong if the install completed and you booted into windows.... or did you run the install from inside windows?

---

### Post by bangbang023 on 2010-05-03
Ran the installer after booting off of the disk. I selected the 100gb I had taken away from Disk 2 for the installation and another 5gb off of Disk 0 for swap space.

---

### Post by frantid on 2010-05-04
If everything completed and it told you to reboot, then I suspect grub got installed onto the wrong drive.  Can you boot of the live cd and run the bootinfoscript?  see here for a how to:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

---

