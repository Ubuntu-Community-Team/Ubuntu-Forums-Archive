---
title: "No bootable device - insert boot disk"
date: 2019-03-06
forum: Installation &amp; Upgrades
---

### Post by duncan9 on 2019-03-06
Hi All,

I have a Toshiba Satellite C855-29M with, currently, no operating system. I'm trying to install Ubuntu on it using a USB drive but continually get the 'No bootable device message'.

The BIOS is InsydeH20 and is System BIOS Version 6.70. 

I've tried three keys now but none work - although do work on other laptops. Any ideas?

Thanks in advance, Duncan

---

### Post by oldfred on 2019-03-06
Are you selecting in UEFI the flash drive? 
It should show two boot options, one UEFI and one BIOS, if USB flash drive seen correctly from f12 UEFI boot menu.
Some UEFI may need UEFI Secure boot off, and separately allow USB boot.

Have you updated UEFI to latest version.
How did you make flash drive?
Some have had issues with some tools to make flash drive, some have had issues with some flash drives or some USB ports.
       Lots of info on USB boot for installing
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
Ubuntu install guide - multiple ways to create live installer to flash drive
[URL="https://help.ubuntu.com/community/Installation"]https://help.ubuntu.com/community/Installation

      [/URL]
 Toshiba Satellite - turned Secure boot off in Boot-Repair update & UEFI
[https://ubuntuforums.org/showthread.php?t=2346022](https://ubuntuforums.org/showthread.php?t=2346022)
[http://ubuntuforums.org/showthread.php?t=2317643](http://ubuntuforums.org/showthread.php?t=2317643) 
    [URL="https://help.ubuntu.com/community/Installation"]
[/URL]

---

### Post by duncan9 on 2019-03-07
Hi oldfred,

Thanks for your reply. I only seemed to have the BIOS option and there was no UEFI option under security.

In the end, I took the hard drive out and put it in another machine. Installed on that and then put the hard drive back in the Toshiba. A round about way but seemed to work!

Thanks, Duncan

---

