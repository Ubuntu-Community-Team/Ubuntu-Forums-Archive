---
title: "Can't boot in UEFI"
date: 2013-04-22
forum: Installation &amp; Upgrades
---

### Post by m12 on 2013-04-22
I need help booting in uefi for dual boot windows 8.
I first tried on a dvd, but my bios didn't recognize that as bootable.
I then tried on a usb flash drive with secure boot.  Error message, "The signature check is invalid."
I turned off secure boot.  Error message, "The selected boot device failed."
I selected boot from efi file.  /EFI/BOOT/BOOTx64.EFI return boot device failed. same with grubx64.efi
I tried from a USB hard drive. same results.
Ubuntu 12.04.2 LTS.
Any suggestions?

---

### Post by BlinkinCat on 2013-04-22
Hi,

I assume you have read this guide -

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Good luck - :)

Edit - oldfred would be able to give you a detailed guide on dual booting if he comes across this thread.

---

### Post by m12 on 2013-04-22
> **BlinkinCat said:**
> Hi,

I assume you have read this guide -

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI).
Yes, I have.

---

### Post by oldfred on 2013-04-22
Do you have 64bit version, secure boot off, fast boot off and a valid install to flash drive, check with md5sum? Even some flash drives can cause issues.

 You will need to use the 64 bit version of 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)
Installing Grub for UEFI secure boot is only possible if you have booted your system using EFI. 

      
 Post #14 some flash drives that did not work
[http://ubuntuforums.org/showthread.php?t=2120196](http://ubuntuforums.org/showthread.php?t=2120196)
More tests Flash drives post #5
[http://ubuntuforums.org/showthread.php?t=2130234](http://ubuntuforums.org/showthread.php?t=2130234)

      
 [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by m12 on 2013-04-22
I do have the 64-bit version, and have tried with secure boot on and off.  My bios does not have a quick boot or fast boot setting - if it did, i would have tried both ways.
I read somewhere that creating the partition in ubuntu could mess up windows, and that I should create an unformatted partion where I want it.  Should I delete?

My md5 test shows the download to be wrong.  How come I was able to extract it in the first place?

---

### Post by oldfred on 2013-04-23
IF md5sum is off, then it is not a valid download. That does happen and it can be just a minor internal error that does not show up in the extraction, but since booting is so critical a minor error can totally prevent system from working.

---

### Post by m12 on 2013-04-23
OK, after 5 more tries, i got one with the right md5 and sha1 sums.  BTW, the file /pool/main/g/grub2-signed/grub-efi-amd64-signed_1.9~ubuntu12.04.3+1.99-21ubuntu3.9_amd6_***4***_.deb is named grub-efi-amd64-signed_1.9~ubuntu12.04.3+1.99-21ubuntu3.9_amd6.deb.  I copied it to the same directory with new name because i wasn't sure what the bootloader/installer would want it to be named.

---

### Post by oldfred on 2013-04-23
Good Catch.

I did not have 12.04.2 and do not boot with UEFI. I checked 13.04 and it is amd64 and I just downloaded a copy of 12.04.2 and it is missing the 4. 

I think that is why I have been having to tell many to turn secure boot off to boot when Ubuntu says it should work with secure boot on. Then Boot-Repair fixes the files by downloading the correct one's after install.

Do you want to file the bug report, I have not checked to see if anyone else found it yet.

---

### Post by m12 on 2013-04-23
I don't know how to file a bug report.  I just installed it this morning.  (Though, I've been using 10.04 in a vm for a few months)

---

### Post by oldfred on 2013-04-23
I did not know where to report it, so I just reported it.
If you add your name to it, it helps as the more that post the better the response.
But I doubt they will fix it, but maybe 12.04.3 will.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1172065](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1172065)

You do have to create another login in launchpad if you do not have one.

       bug reports info on how to do:
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)
[https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)

---

### Post by Gobtron on 2013-04-23
I had problems too, few days ago, in order to boot from a usb key. I used Pendrive to make the bootable device. I first tried in windows XP, on my old system and that didn't work.

I then tried on Win8, with the option "Set a Persistent file size for storing changes". I set it to 4089 MB

It worked. I can boot from the device.
 
Is that the fact that I made it on Win8 (wich is 64 bit, and not XP) or the fact that I used this option... I don't know.

I wish you better luck than me, cause now, I can boot, but there's a weird sound coming out of my laptop when lauching the installation with "nomodeset=1". I decided to abort!

---

### Post by oldfred on 2013-04-24
Screenshot with missing 4 shown.

---

