---
title: "Installing Lubuntu 'Something' Else'"
date: 2018-08-24
forum: Installation &amp; Upgrades
---

### Post by vashsgirl on 2018-08-24
I've been trying to install Lubuntu 18.04 from a USB alongside Windows 10. I followed a guide to shrink the partition from the Windows disk manager. The guide said to name it E:/. When i run the Lubuntu setup, it skips the regular Installation Type screen and goes directly to the Something Else option screen. In the table, all it shows is /dev/sda. And under boot loader, the only option is /dev/sda Generic Flash Drive. Did I make a mistake shrinking? I'm not sure where i went wrong. Thanks in advance for your help!

---

### Post by ajgreeny on 2018-08-24
Did you actually create the partition using Windows 10? That will usually not work for Linux as it probably is a Windows dynamic partition, unusable by the Linux OS.

All you need to do is create some unallocated space on the drive by deleting that new partition, which you can now do in the live Ubuntu OS using gparted (if it can see it) as you have already safely shrunk Windows from its own utilities, then use the "Something Else" option and the unallocated space should now show.

---

### Post by yancek on 2018-08-24
If all you see when you get to the partitioning on installing Ubuntu is your flash drive, the most likely situation is that you have left your windows 10 in default status of hibernation.  You would need to boot into windows and turn off fast boot and anything related to hibernation as no Linux system will mount a hibernated system so it obviously then will not show during the install.

Also better to create unallocated space rather than a partition for Ubuntu from windows as suggested above.

---

### Post by vashsgirl on 2018-08-24
Thanks for the replies! Before i try anything else, I'd just like to add a couple things. I've already disabled Hibernate, Fast boot and Secure boot in Windows. Also, please check the following imgs for clarification.

[https://www.flickr.com/photos/156189310@N07/shares/044s53]("https://www.flickr.com/photos/156189310@N07/shares/044s53")

Should i proceed with gparted? Or try the unallocated space method?

---

### Post by vashsgirl on 2018-08-26
I went back into Windows Disk Mgmt and deleted the volume I'd created for Lubuntu. Now it just reads as unallocated space. I tried the Lubuntu installer again, and it goes to the same Something Else screen with no options, as shown in the pic linked to above. Can anyone help?

(Using Dell xps 9370)

---

### Post by SeijiSensei on 2018-08-26
Looks to me like both drives appear in the image on the right.  It's a bit too blurry to be readable, though, so I could be wrong.

---

### Post by yancek on 2018-08-26
The images you posted are too blurred to read (for me at least) and I can't even tell if it is UEFI or Legacy.  I expect UEFI but...?  I would suggest that you read the link below on dual booting Ubuntu systems with windows in UEFI.  You should see the same options in Lubuntu as I believe it also uses the Ubuntu installer.  You might see different background colors and you should use the manual "Something Else" method.

 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by vashsgirl on 2018-09-09
Thank you both for your replies. I haven't have the patience or time to straighten this out. :P
Until today. After starting from the link Yancek provided, i clicked and read and searched until i found a suggestion to change from RAID to AHCI in BIOS according to the Alternative Method found here:

[https://www.askvg.com/how-to-change-sata-hard-disk-mode-from-ide-to-ahci-raid-in-bios-after-installing-windows/]("https://www.askvg.com/how-to-change-sata-hard-disk-mode-from-ide-to-ahci-raid-in-bios-after-installing-windows/")

Seems to be working! I've installed Lubuntu alongside  Windows 10 and am now updating. Thanks a lot for your help!
PS I'm sorry about the pics. They must have lost something in the transfer. I reuploaded them here in case anyone is having a similar issue:

[https://www.flickr.com/photos/156189310@N07/]("https://www.flickr.com/photos/156189310@N07/")

---

