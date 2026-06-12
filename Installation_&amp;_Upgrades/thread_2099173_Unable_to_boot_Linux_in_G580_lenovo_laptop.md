---
title: "Unable to boot Linux in G580 lenovo laptop"
date: 2012-12-28
forum: Installation &amp; Upgrades
---

### Post by henrythung on 2012-12-28
hi there, I am trying to install linux on my G580 lenovo laptop, and the default factory setting of the laptop has four primary partitions. I removed one primary partition and create logical partition to install Ubuntu LTS. I choose /dev/hda for the boot loader installation, and install linux in /dev/hda5. The installation completed successfully and I restart the pc. However there are no option for the linux OS when the computer is restarted, there are only one option for Window 7. For your information, I am using 64 bit OS. Any solution?

Thanks.

---

### Post by oldfred on 2012-12-28
Welcome to the forums.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:

[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by henrythung on 2013-01-04
hi, attached is the requested boot log file. I don't have internet connection when i restart my pc with ubuntu usb disk, thus can not upload the log file. For your information, I have tried to use "easyBCD" to try to add linux boot up selection, but it can not detect my installed linux setting....
Please let me know what to do next.
Thank you very much!

---

### Post by YannBuntu on 2013-01-04
hi
please follow this procedure: [https://help.ubuntu.com/community/InstallingUbuntuOnBigDisk](https://help.ubuntu.com/community/InstallingUbuntuOnBigDisk)

---

