---
title: "Installing UM 16.10 to sda2"
date: 2017-05-11
forum: Installation &amp; Upgrades
---

### Post by raleigh3 on 2017-05-11
I am trying to install UM 16.10 to sda2.
  However I am bogged down at the format step.
  
Version 16.04 is on sda1 which I want to keep.

  
It wanted to erase files on sda1 so I aborted the install.

---

### Post by raleigh3 on 2017-05-11
I could use some help.

I tried to take some screenshots but it won't let me save them to a pen drive or my other partition.

---

### Post by Dennis N on 2017-05-11
On the Installation Type screen, use the "something else" option and continue to the partitioning screen. Select the partition you want to use for root partition of the new install. Then click the change button under the partition display and fill in the details in the pop up window. Then you should be able to proceed.

---

### Post by yancek on 2017-05-11
If you are using the manual "Something Else" option in the installer, you would select /dev/sda2 in the main installer window, select the mount point from the drop down arrow as "/", then select to format sda2 and decide where you want the boot loader installed.  Make sure you do NOT select the format check box for sda1.  The default is /dev/sda which would mean the master boot record if you are using the older MBR install.  Do you have any other OS besides 16.04 and are you using UEFI?

If you are not using the Something Else option, I don't think one of the 'auto-install' options are going to work.
If you can't resolve this, more details on which installation type option and steps taken would be useful.

---

