---
title: "Install to external drive"
date: 2015-10-22
forum: Installation &amp; Upgrades
---

### Post by findingthebalance on 2015-10-22
Trying to do a full install Ubuntu 15.10 onto an external usb HD, after going through setting up partitions and install and selecting the drive from the boot menu it refuses to boot into the drive. I have never had this problem before. Is it no longer possible?

---

### Post by oldfred on 2015-10-22
UEFI or BIOS?

Best to see details:
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by findingthebalance on 2015-10-22
Well I give up, I have tried half dozen ways to install it to external drive with no success and from what I have read it looks like it's a no go anyways. There should be option to just pick a drive, format it and install. On another note ... Can anyone dual boot Ubuntu with Windows anymore?

---

### Post by oldfred on 2015-10-22
I have full installs of Ubuntu installed to flash drive as sdc drives in both UEFI & BIOS boot modes. UEFI is a bit more difficult.
But if you partition in advance and install grub to sdb it works for BIOS. With UEFI you have to copy some files.
But you need to use Something Else install option.

 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screeens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
Linux on UEFI: A Quick Installation Guide
[http://www.rodsbooks.com/linux-uefi/](http://www.rodsbooks.com/linux-uefi/)
Something Else or manual Install
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)

---

### Post by findingthebalance on 2015-10-22
I have Ubuntu 15.04 installed on my internal hard drive and it's in legacy mode.

---

### Post by yancek on 2015-10-22
So you have two drives, one internal with 15.04 and one external with 15.10.
You can boot 15.04 which is the only operating system on the drive.
You cannot boot 15.10 which is the only operating system on the external.

Did you use the manual (Something Else) option to install to the second disk?
Did the second disk show in the Installation Type window during the the install of 15.10?
Did it show up as /dev/sdb or a different device name?
Did you select to install the Grub bootloader files to the MBR of /dev/sdb, your external drive?
If so, did you change the boot priority in the BIOS to boot from the second drive?
If you did not install the Grub bootloader to the MBR of the second drive, where did you install it, and also did you run sudo update-grub from 15.04?

---

