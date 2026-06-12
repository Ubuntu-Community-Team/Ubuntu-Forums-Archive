---
title: "Dual booting ubuntu and windows 8 problems"
date: 2012-11-03
forum: Installation &amp; Upgrades
---

### Post by smooth_dudes on 2012-11-03
Hello there


I have recently purchased an asus ux32vd. After purchase i deleted the pre-installed windows 7, and installed ubuntu. This laptop comes with a 32gb ssd, and a 500gb hdd. I installed ubuntu on the sdd, and left the 500gb as nfts in case i wanted to install windows. I have since gotten my hands on windows 8, and are now trying to install it on the hdd.

This however is not very easy. First time i tried, it told me that i couldt not install windows on a GPT partition table. So i created a new partition table, only now windows tells me that "We couldn't create a new partition or locate an existing one.  For more information, see the Setup log files."
Searching google i found that this is often caused be some external device being plugged in. I have however no external devices plugged in, except for the usb i am using to install windows with.

So i thought that maybe the ssd was the problem, or maybe it is my partition setup in general. So my question is really, if anyone have tried something similar themselves, or if anyone can recommend a good way to do this?

Kind regards.

---

### Post by oldfred on 2012-11-03
I do not know Windows 8, but Windows only installs to gpt if you boot installer in UEFI mode. Did you install Ubuntu in UEFI mode on SSD? Both system need to be either UEFI/gpt or BIOS/MBR but not mixed.

Windows Recommended UEFI-Based Disk-Partition Configurations
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Change the booting style of Windows Vista or 7 x86_64 versions from BIOS-MBR mode to UEFI-GPT mode without formatting or reinstalling
[https://gitorious.org/tianocore_uefi_duet_builds/pages/Windows_x64_BIOS_to_UEFI](https://gitorious.org/tianocore_uefi_duet_builds/pages/Windows_x64_BIOS_to_UEFI)
Windows installs the efi bootloader to (ESP)/EFI/Microsoft/Boot/ which is identical to (WINDOWS_SYSTEM_PART)/boot/microsoft/ incase of BIOS systems.

---

### Post by critin on 2012-11-03
> **smooth_dudes said:**
> Hello there

Searching google i found that this is often caused be some external device being plugged in. I have however no external devices plugged in, **[COLOR=Red]except for the usb i am using to install windows with.[/COLOR]**

So i thought that maybe the ssd was the problem, or maybe it is my partition setup in general. So my question is really, if anyone have tried something similar themselves, or if anyone can recommend a good way to do this?

Kind regards.

 > **[COLOR=Red]except for the usb i am using to install windows with.[/COLOR]**This sounds like it might be the  consumer/review release.

If this is the upgrade version Win8,  the $40, $20, or free preview,   it can only be installed on a partition/disk that held a previous version of Windows.    It's for upgrading only.  If it's a regular store copy, previous installation doesn't apply.

 > and left the 500gb as nfts

Is this where win7 was originally installed?  If so, and it wasn't reformatted, the upgrade will work, so all I've said won't apply.  Good luck.

---

### Post by smooth_dudes on 2012-11-03
> **critin said:**
> This sounds like it might be the  consumer/review release.

If this is the upgrade version Win8,  the $40, $20, or free preview,   it can only be installed on a partition/disk that held a previous version of Windows.    It's for upgrading only.  If it's a regular store copy, previous installation doesn't apply.

 

Is this where win7 was originally installed?  If so, and it wasn't reformatted, the upgrade will work, so all I've said won't apply.  Good luck.

No the disk has been reformatted, but indeed i was using the consumer preview. I am going to try with windows 7 professional instead, and hope that will work better.

Thank you both for the help.

---

