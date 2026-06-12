---
title: "Boot Issue after installing 16.04 on UEFI laptop"
date: 2018-04-26
forum: Installation &amp; Upgrades
---

### Post by derek_stewart2 on 2018-04-26
I've just installed 16.04.4 on a laptop that had windows 8.1 and UEFI. I disabled Fast Boot and Secure Boot prior to installation. I opted to erase the entire disk. Now when i boot up the laptop I receive a black screen with the following message:

Default Boot Device Missing or Boot Failed
Insert Recovery Media and Hit Any Key
Then Select 'Boot Manager' to choose a new Boot Device or to Boot Recovery Media
OK

I click on "OK" and it then take me to a Boot Manager screen with Boot Options
1 Unknown Device (lists the HDD "serial number")
2 grubx64efi

After selecting the first option the GRUB screen appears and boots into Ubuntu normally.

I've run Boot Repair but the same sequence occurs on booting.

Any suggestions on how I can fix/remove the initial error?

---

### Post by linux4me on 2018-04-26
When you booted to the USB to do the install, did you select the USB as UEFI? Often, a boot menu will show the Ubuntu USB stick as both a regular (MBR) and UEFI option, and you must select the UEFI option if you have the BIOS set to boot UEFI.

---

### Post by derek_stewart2 on 2018-04-26
Installed from a DVD. Just selected the drive from the boot options. I ran a check through terminal and it came back with "Installed in UEFI."

---

### Post by yancek on 2018-04-26
Did you change the boot priority in the BIOS back after the install to set the HD first?  If you've been trying boot repair, why haven't you posted a link to the output here so people more familiar with booting problems could take a look at it?

---

### Post by derek_stewart2 on 2018-04-26
Ah, of course, senior citizen moment. I had scribbled down the URL on a post-it but someone must have thrown it away while I was at work today. I've just run it again and got the following URL:

[http://paste.ubuntu.com/p/qSxrRS22Yv/](http://paste.ubuntu.com/p/qSxrRS22Yv/)

---

### Post by oldfred on 2018-04-27
Two things.
I see Secure Boot on, but trying to boot grubx64.efi. For Secure Boot systems, you use shimx64.efi.
Probably easier just to turn UEFI Secure Boot off (but see next first).

I see Acer. 
All models of Acer have a unique requirement of setting "trust" from inside UEFI.
Many have also had to update UEFI to latest version from Acer.

       Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392)

---

### Post by derek_stewart2 on 2018-04-27
Thanks oldfred. The second link gave me the solution.

I've had a few issues down through the years of using Ubuntu and come here - it never fails to provide a solution.

---

