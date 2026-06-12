---
title: "Ubuntu will not boot from USB but Debian does"
date: 2013-12-14
forum: Installation &amp; Upgrades
---

### Post by ronniepinsky on 2013-12-14
Edit:  Problem fixed.
Here is what to take away from this.
1.Rufus will make an Ubuntu install USB drive in such a way that some systems will boot and some will not.  usb-creator is more universal.
2.Freeze at Ubuntu boot menu and system restart means the usb-creator install did not go correctly.  Reformat manually and try again being sure to enter your password carefully when it needs to write to the master boot record.
3.Random errors, especially drive related, on boot means that the drive is probably bad.

-----

I have setup a USB flash drive for booting Ubuntu with the Windows tool, Rufus.  I chose to format as FAT32 and MBR setup for BIOS and UEFI.  This flash drive will not boot on a particular computer, but is working because a different computer will boot it.  The computer that does not boot Ubuntu **will** boot a Debian USB installer.  The Debian flash drive is setup in Linux with by using zcat to transfer the boot.img.gz and then copying the installer ISO over.  I have eliminated the problem being with the individual flash drive itself as well.[br]1[/br][br]1[/br]The files are noticeably different between drives.  The Debian installer has more files in the root of the drive like "initrd.gz" and "linux".  Obviously they seem to be using different techniques to boot.  I am guessing the Debian installer is using a more compatible method?[br]1[/br][br]1[/br]Please help with this because I would like to install Ubuntu instead and I don't like the inconsistency in this situation.

---

### Post by sudodus on 2013-12-18
Have a look at the following web page with a lot of tips and methods [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

