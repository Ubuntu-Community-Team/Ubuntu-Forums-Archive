---
title: "Dual-boot 16.04 with Windows 10 fails"
date: 2017-05-01
forum: Installation &amp; Upgrades
---

### Post by previous on 2017-05-01
I recently purchased an ACER ATC-780 (desktop) with Windows 10 installed. I installed Ubuntu from a disk image of 16.04.2 beside the W10 in a 240GB partition. The installation seemed to complete normally but when it rebooted after installation it booted into Windows. The "BIOS" is listed as A01-AO. The C: drive on windows is 240 GB smaller indicating the a net partition was actually created. What can i do to get the machine to boot into GRUB? I have in stalled both SuSE and Ubuntu on a few older machines but this is my first attempt on one using UEFi.

---

### Post by yancek on 2017-05-01
Read the Ubuntu documentation on dual booting uefi at the link below.  Did you follow the steps indicated.  Obviously, it would have been better to read this before starting. 

 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

If the information at the link above doesn't help, go to the site below and get the boot repair software.  I would suggest that rather than trying to repair you simply select the option to Create BootInfo Summary and post a link to the output.  Someone here should then be able to suggest a solution.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by oldfred on 2017-05-02
All Acers we have seen require you to set a UEFI supervisory password & enable "trust" from within UEFI on the .efi boot files in /EFI/ubuntu.
This is unique to Acer but better than some of the workarounds required with other brands.
Also make sure you have newest UEFI from Acer.

 Acer Trust Settings - details:
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
[http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392)
 InsydeH20 setup utility
Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)

---

### Post by previous on 2017-05-02
Thanks oldfred.  I followed the steps listed in [https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003) and successfully installed a "BIOS" password and enabled secure boot.  However, I could not select secure boot nor could I find any way to select a boot file.  The "BIOS" different than the one described in the link and must be entered by using the del key instead of F2. It probably requires a different series of steps to select a boot file.  Any additional suggestions you might have would be appreciated.

---

### Post by oldfred on 2017-05-02
Normally UEFI Secure Boot is on, and you want to turn it off. Some systems only let you do that when you have the UEFI password set. (never lose that password or reset when done).
And many systems do not call it Secure boot. It is often "Windows" and "Other" where even if you want Windows 7 you have to use "Other" as Windows 7 does not support Secure Boot.

Several different threads seem to explain it slightly differently. But perhaps you have a new UEFI from Acer? What brand UEFI, does it still say Insyde?
But it cannot be too different as system is still Intel based.
Often you have to look at various screens. My self build system with a Gigabyte motherboard does not require a password, but settings are in various screens and some do not open up more settings until you change a different one. Sometimes even in a different tab in the UEFI.

If still lost you can post screen shots. Most new UEFI let you also take screenshots and save to drive. Or use camera. In forums' Advanced Editor is a paperclip icon to attach photos.

---

### Post by previous on 2017-05-03
The BIOS screens are labeled "BIOS setup utility Version 2.17.1255 Copyright (C) 2002-2016 ACER inc".  This suggests to me that it is an ACER produced BIOS. When I have a bit more time, I will run Ubuntu Live and pursue the Boot Repair/Analysis.

---

### Post by waterresistro on 2017-05-05
Same thing here, with v2.18.1263, i don't have the "select UEFI trusted file" option that all threads talk about.

---

### Post by previous on 2017-05-07
I too did not have the "select UEFI trusted" choice  on the ACER ATC 780. I have been unable to install Ubuntu along with Windows 10 but once I managed to make a USB boot drive I was able to find a work-around.  I disconnected the CD drive and installed a second hard drive. (The ATC 780 motherboard has only two SATA connectors but the case has one vacant spot for a hard drive). After Ubuntu was installed by itself on the second hard drive the "BIOS" was able to find GRUB and could select between the two operating systems. I'm going to mark this "solved" even though the original problem still exists.

---

