---
title: "Problem to install Ubuntu"
date: 2016-03-30
forum: Installation &amp; Upgrades
---

### Post by kfule on 2016-03-30
[FONT=arial]Imtrying to do dual boot Windows 10 - Ubuntu 14.04. With Live CDor Ubuntu 14.04 Flash Drive

Thisis what i got:
"Theapplication or operating systemcould not loaded becouse required file missing or conteins error.Oxc000007b" 
MyLaptop is: Asus x551 Mav, bougt it with Windows 8.1   Thanks.[/FONT]

---

### Post by slickymaster on 2016-03-30
*Moved to the ***Installation & Upgrades*** sub-forum*

---

### Post by oldfred on 2016-03-30
That sounds more like a Windows error?

You have to boot flash drive from UEFI boot menu. It may show flash drive twice, one UEFI:flash and other flash drive by name/label or BIOS.

Did you verify ISO was downloaded correctly with md5sum?
       [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) 
    
 [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
these should then work:
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[URL="https://wiki.ubuntu.com/Win32DiskImager/iso2usb"]https://wiki.ubuntu.com/Win32DiskImager/iso2usb

      [/URL]
 If UEFI only, then can just extract ISO with 7-zip to FAT32 formatted drive with boot flag on FAT32 partition.
Will not boot in BIOS mode
UEFI only USB key, just extract ISO ( 7 zip or similar) to FAT32 formated flash & set boot flag.
[http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media](http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media)
UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040) 

 Use Windows own Disk tools to shrink the NTFS partition to make unallocated space. Reboot immediately so Windows can run chkdsk and update to its new size. Make sure fast start up is off in Windows.
Often better to have Secure boot off in UEFI and fast boot in UEFI off.

Vendors have same UEFI across many models, so these may be the same or very similar:

 Asus M32CD desktop - Skylake several boot parameters required
[http://ubuntuforums.org/showthread.php?t=2312977](http://ubuntuforums.org/showthread.php?t=2312977)
ASUS G752 Can't see SSD NVMe Needed UEFI/BIOS update
[http://ubuntuforums.org/showthread.php?t=2307273](http://ubuntuforums.org/showthread.php?t=2307273)
ASUS ROG GL552VW-CN104T
[http://askubuntu.com/questions/694453/new-laptop-skylake-cannot-boot-xubuntu-even-with-boot-parameters](http://askubuntu.com/questions/694453/new-laptop-skylake-cannot-boot-xubuntu-even-with-boot-parameters)
Problems Installing on ASUS F555U   needed boot option pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2303665](http://ubuntuforums.org/showthread.php?t=2303665)
Installing 15.04 on Asus N550JX, boot parameters required
[http://ubuntuforums.org/showthread.php?t=2293394](http://ubuntuforums.org/showthread.php?t=2293394)

Update:
Is this a Bay Trail Intel Chip?
Issues with Bay Trail:
[http://ubuntuforums.org/showthread.php?t=2314964](http://ubuntuforums.org/showthread.php?t=2314964)
 Many Intel Bay Trail Devices Have Been Borked On Linux For The Past Year - Mar 2016
[http://www.phoronix.com/scan.php?page=news_item&px=Intel-Linux-Bay-Trail-Fail](http://www.phoronix.com/scan.php?page=news_item&px=Intel-Linux-Bay-Trail-Fail)

---

### Post by X-RED_Tech on 2016-03-30
[http://www.tomshardware.co.uk/answers/id-1991597/windows-bit-error-0xc000007b.html](http://www.tomshardware.co.uk/answers/id-1991597/windows-bit-error-0xc000007b.html)

Definitely a typical Windows error. Just run chkdsk.

---

