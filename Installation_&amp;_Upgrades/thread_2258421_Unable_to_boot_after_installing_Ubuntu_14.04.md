---
title: "Unable to boot after installing Ubuntu 14.04"
date: 2014-12-27
forum: Installation &amp; Upgrades
---

### Post by amitaihoze on 2014-12-27
Hi, I installed Ubuntu 14.04 on my desktop computer, and got this message:
Reboot and select proper boot device or insert boot media in selected boot device and press a key

My BIOS is MSI click BIOS II (2). It uses UEFI. Actually it has a menu for choosing between two modes: "UEFI" and "UEFI and Legacy".
The first one just sends me back to the BIOS menu and the second gives the above error message.

I followed [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI).
 Fastboot and MSI Fastboot are diabled there, couldn't find Quickboot or secure boot or Intel Smart Respone Technology.
Found Intel Smart Connect Technology instead and disabled it.
Still didn't work.
I ran boot repair the recommended way and got this url
[http://paste.ubuntu.com/9630811](http://paste.ubuntu.com/9630811)

But still the same message appears.

Please help,
Thanks, Amitai.

---

### Post by oldfred on 2014-12-27
You have installed in Legacy/BIOS/CSM boot mode.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

Usually with UEFI, there are three modes, UEFI with secure boot, UEFI without secure boot and CSM/Legacy/BIOS. 
And how those modes are enabled varies greatly by vendor. And if secure boot is on, then it will not boot in standard UEFI nor BIOS boot modes. And BIOS boot mode has no secure boot mode.

How you boot install media either UEFI or BIOS is how it installs, so you booted flash drive in BIOS boot mode.

Double check that you have turned off secure boot. On my system it was called "Windows" or "Other OS" with no mention of secure boot, but that was what that setting was.

Also when you turned off Intel SRT, did you set drive to AHCI mode?

---

