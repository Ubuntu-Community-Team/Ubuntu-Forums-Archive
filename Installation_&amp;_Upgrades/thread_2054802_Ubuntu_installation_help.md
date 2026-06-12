---
title: "Ubuntu installation help ?"
date: 2012-09-08
forum: Installation &amp; Upgrades
---

### Post by Aclockhead on 2012-09-08
I need help with the installation process .i have been trying to install  it for a while now and have failed to so twice so every time I switch  my pc on it gives a menu form where i have to select the windows in the  menu there is windows 7 and two ubuntu choices which if i select gives a  screen showing some error. I tried again today by going to the boot  menu and selecting the disc from the menu now after some time in the  installation process i am faced with a problem something about  partitioning  here is the screen  :[http://s1060.photobucket.com/albums/t450/AClockhead/](http://s1060.photobucket.com/albums/t450/AClockhead/) and i have no idea  what to do here ya and i have windows 7 already installled which i dont  plan to remove .

---

### Post by balajimailers on 2012-09-08
[QUOTE=Aclockhead;12225320]I need help with the installation process .i have been trying to install  it for a while now and have failed to so twice so every time I switch  my pc on it gives a menu form where i have to select the windows in the  menu there is windows 7 and two ubuntu choices which if i select gives a  screen showing some error. I tried again today by going to the boot  menu and selecting the disc from the menu now after some time in the  installation process i am faced with a problem somet

---

### Post by darkod on 2012-09-08
Boot with the cd and when the menu comes up about how to install, select Something else. That will show the manual partitioning step you posted a picture of.

In that step, first select the /dev/sda6 partition and click the button Change below. In the window that opens select Use As ext4, mount point / and tick the format box. Close the window.
Then click the /dev/sda5 partition and again the Change button. For that partition in the Use As select swap area. There is no mount point to select for swap. Close the window.

When you are back at the partitions list, under the list is the drop down menu to select the device for the bootloader. Select /dev/sda, not /dev/sda6. The bootloader grub2 needs to go to the MBR of the disk.

That's it.

---

