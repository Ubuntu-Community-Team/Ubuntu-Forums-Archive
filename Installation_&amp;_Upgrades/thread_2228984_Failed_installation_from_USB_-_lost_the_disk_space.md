---
title: "Failed installation from USB - lost the disk space I had reserved..."
date: 2014-06-10
forum: Installation &amp; Upgrades
---

### Post by Mats_Lindqvist on 2014-06-10
I tried Ubuntu from a USB-boot. I liked it, so I decided to install from that USB. During installation (parallel with Windows Vista) I got an error message saying there is something wrong with my USB-stick. The installation thus failed. Now when I go back to Windows I seem to have lost the disk space that I reserved for the Ubuntu installation (20 GB if I remember correctly). Now I am running a proper installation, not from the USB-stick. I hope this will work. Is there any chance I can recover that lost disk space? I don't have an awful lot of it now...For the new installation i reserved 6 GB. 

* Edit *
I have now tried to install Ubuntu the "proper way" using the *.iso file located on the hard drive in Windows. During boot I get the error message "Serious errors were found while checking the disk drive for /. Press I to ignore, S to skip mounting or M for manual recovery." Neither of those options can help me (with my limited Linux knowledge) resolve this error. So now I have wasted 26 GB of disk space, and, as it seems, is unable to intall Ubuntu. can anyone help out with this?

Best regards Mats Lindqvist

---

### Post by oldfred on 2014-06-10
Normal install is from a flash drive or DVD. Not sure what you are using for an ISO inside Windows, wubi? Wubi is being discontinued and few know it. Last supported version is 12.04.

 Also instructions for DVD or USB flash drive
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to flash or DVD.
[https://help.ubuntu.com/community/USB%20Installation%20Media](https://help.ubuntu.com/community/USB%20Installation%20Media)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by Mats_Lindqvist on 2014-06-11
Thanks oldfred, I'll try DVD next. I "solved" the lost disk space problem by deleting the Ubuntu partitions that were created during the installation, using Windows disk management tool. I then had to use a third party software to merge the free disk space with the "C:"-partition in Windows. I'm not in front of that computer now, but I think it was this one: [http://www.partition-tool.com/](http://www.partition-tool.com/)

---

### Post by oldfred on 2014-06-11
Always best to use Windows partition tools to shrink the Windows partition to make unallocated space for Ubuntu install. And always reboot Windows immediately after any change so it can run chkdsk and make its repairs for its new size. But never create new partitions with Windows tools, it may convert to dynamic partitions which does not work with Linux.

Most of the third party Windows tools for partitioning are better than Windows own tools, but still use gparted if working with Linux partitions.
Use Windows tools for Windows and Linux tools for Linux.

---

