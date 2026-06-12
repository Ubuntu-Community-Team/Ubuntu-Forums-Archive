---
title: "Ubuntu USB installer won't boot in HP Ultrabook Folio 9470m"
date: 2013-03-18
forum: Installation &amp; Upgrades
---

### Post by rontynen on 2013-03-18
I have Windows 7 Home Premium (Version 6.1 Build 7601: Service Pack 1) installed in my laptop and I am trying to install Ubuntu alongside Windows. I have reserved a 60 GB hard drive partition for Ubuntu using Windows's own partitioning tool. The device manager says I have i5-3427U processors and I checked from the Intel's webpages that these processors are 64-bit. Therefore I concluded that I should install the 64-bit version of Ubuntu.

 I created the USB installer according to the instructions given here: [https://help.ubuntu.com/community/Installation/FromUSBStickQuick](https://help.ubuntu.com/community/Installation/FromUSBStickQuick). I checked in BIOS Boot options that the 'USB device boot' box is checked and in the 'Legacy Boot Order' list I moved USB Floppy, USB CD-ROM and USB Hard Drive on top. The computer doesn't recognize the USB installer and always goes on to boot Windows. I also tried checking the boot device options by pressing F9 but no USB devices were listed. I tried the installer in my friends laptop and it worked normally.

 I have tried both Ubuntu 12.04.2 (ubuntu-12.04.2-desktop-amd64.iso) and 12.10 (ubuntu-12.10-desktop-amd64.iso) versions. I have also tried creating the installer using Universal USB Installer, LiLi USB creator and Unetboot, but nothing works. I checked the USB boot compability of my laptop by running the memtest from the USB stick ([http://www.pendrivelinux.com/testing-your-system-for-usb-boot-compatibility/](http://www.pendrivelinux.com/testing-your-system-for-usb-boot-compatibility/)) and it worked normally.
   
 I'm not an expert on computers but I tried everything I could to narrow down the problem. The information I found on the web doesn't get me any further so any help would be greatly appreciated. I would also be interested to know if it is better to install Ubuntu 12.10 or would 12.04.2 be a safer option.

---

### Post by sudodus on 2013-03-18
Welcome to the Ubuntu Forums :-)

This might work if the USB pendrive is recognized as a hard disk drive.

Insert the USB pendrive, and enter the bios menus again. Change the boot order between the hard disk drives (HDDs). Save and reboot.

Good luck!

---

### Post by rontynen on 2013-03-18
I have given priority to all USB boot options (my message above) if that is what you mean. I even tried to uncheck all the other BIOS boot options except the USB device boot, but my computer still boots Windows.

---

### Post by sudodus on 2013-03-18
> **rontynen said:**
> I have given priority to all USB boot options (my message above) if that is what you mean. I even tried to uncheck all the other BIOS boot options except the USB device boot, but my computer still boots Windows.

Yes, I have read that, but some computers do not see USB pen drives as USB devices, but as storage drives, and keep track of them along with the internal HDD(s). I don't know if this is the case with your computer, but I think it is worthwhile to try according to post #2 (my previous post).

---

### Post by rontynen on 2013-03-18
I placed "Notebook mSata Drive" before "Notebook Hard Drive" in BIOS  boot options. I hope that I understood your instructions correctly. The  computer still boots to Windows.

---

### Post by sudodus on 2013-03-18
> **rontynen said:**
> I placed "Notebook mSata Drive" before "Notebook Hard Drive" in BIOS  boot options. I hope that I understood your instructions correctly. The  computer still boots to Windows.

I think an mSATA drive is something else (another sata drive attached to the mSATA interface). Those bios settings are so general!

 Is your Ubuntu install drive a USB pendrive (or stick)? What ***brand name*** is it? Can you see it listed along with the brand name of the internal HDD? In that case, change order between them.

---

### Post by rontynen on 2013-03-18
It is Verbatim V3 USB Drive. I cannot see it listed in the BIOS boot options. Currently my Legacy Boot Order has a following list: USB Hard Drive, USB CD-ROM, USB Floppy, SD Card, Notebook mSATA Drive, Notebook Hard Drive, Notebook Ethernet. I also tried to boot UEFI mode and I placed Generic USB device and USB Hard Drive on top in the UEFI Boot Order. So far nothing works.

---

### Post by sudodus on 2013-03-18
> **rontynen said:**
> It is Verbatim V3 USB Drive. I cannot see it listed in the BIOS boot options. Currently my Legacy Boot Order has a following list: USB Hard Drive, USB CD-ROM, USB Floppy, SD Card, Notebook mSATA Drive, Notebook Hard Drive, Notebook Ethernet. I also tried to boot UEFI mode and I placed Generic USB device and USB Hard Drive on top in the UEFI Boot Order. So far nothing works.

I don't think you'll have any luck with UEFI. I guess from you reply, that you have not found any menu where you can sort or rank your HDDs. That would be another menu, than the one you have been using so far. (And I think you have explored that menu enough to succeed. So the problem is somewhere else.)

You wrote about the USB installer, and that it works in another computer.> I tried the installer in my friends laptop and it worked normally.  Is this the Verbatim V3 USB Drive? I suggest that you get (borrow or buy) another USB pendrive, make it an Ubuntu install drive, and try to boot your computer from it.

The USB pendrives are not exactly the same, and some of them are harder to use as boot drives, so it is quite possible that another pendrive will work with your computer.

---

### Post by rontynen on 2013-03-18
Yes, it was the same Verbatim V3 USB Drive I tried with my friends laptop. I'll try with another pendrive as soon as I get one.

---

### Post by sudodus on 2013-03-18
> **rontynen said:**
> Yes, it was the same Verbatim V3 USB Drive I tried with my friends laptop. I'll try with another pendrive as soon as I get one.
1. I think this is really the first thing to do. I've had good luck with Sandisk and Transcend pendrives, USB2 as well as USB3 drives.

2. You should also try booting from ***different USB ports on your computer. Try all of them***, USB2 as well as USB3.

---

### Post by rontynen on 2013-03-27
> **sudodus said:**
> 1. I think this is really the first thing to do. I've had good luck with Sandisk and Transcend pendrives, USB2 as well as USB3 drives.

2. You should also try booting from ***different USB ports on your computer. Try all of them***, USB2 as well as USB3.

I got myself another pendrive and Ubuntu installed without any problems. Thank you very much for the help!

---

### Post by sudodus on 2013-03-27
> **rontynen said:**
> I got myself another pendrive and Ubuntu installed without any problems. Thank you very much for the help!
You are welcome :-)

---

### Post by banksnld on 2013-07-17
This was supposed to have been fixed in a recent BIOS update:

Version: F.44  (22 May 2013) 
      Fixes 
  - Fixes an issue which causes the system to stop functioning and display a black screen when the system is powered on. 
- Fixes an intermittent issue where changes cannot be made to the system using the F10 BIOS setup. 
- Fixes an issue where the shift key or control key do not function properly and are repeatedly activated after being pressed one time while the system is in the preboot environment or in the DOS environment. 
- Fixes an intermittent issue where a battery that has been fully discharged does not recharge properly. 
- Fixes an issue which causes the incorrect vendor name for the ADATA memory module to be displayed in the F10 BIOS Setup. 
- Fixes issue where system does not boot properly from a Verbatim USB 3.0 drive. 
- Fixes an issue where the system does not power on (boot) correctly after the PXE IPv4 and IPv6 network protocols are disabled in the F10 BIOS Setup. 
- Fixes an issue where the system stops functioning properly and displays a black screen after the lid is closed while the system is powering on and is then opened. 
- Fixes an issue where the right alt and right ctrl keys on a USB keyboard connected to the system do not function properly in the preboot operating system environment.  
 

(Unfortunately, just for the Verbatim flash drives - I'm still having problems booting from a Lexar P10 flash drive.)

---

