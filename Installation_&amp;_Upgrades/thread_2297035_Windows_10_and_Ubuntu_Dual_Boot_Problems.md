---
title: "Windows 10 and Ubuntu Dual Boot Problems"
date: 2015-09-30
forum: Installation &amp; Upgrades
---

### Post by onetome on 2015-09-30
Greetings:

I cannot boot into Ubuntu 15.04 after installing it after Windows 10.

I followed instructions on this page:

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Even disabling the Secure Boot feature. EasyBCD doesn't do anything. 

I did let Ubuntu resize things instead of going through Window's administrative tools to do that.

Windows reported some HDD sector errors, and I got them fixed using ```
chkdsk /r/f
``` or some like code into Window's CLI.

Could someone offer help with this? Thank you. Have spent two+ hours trying to get Ubuntu to work. No dice thus far.

---

### Post by yancek on 2015-09-30
Did you install windows 10 or is it an upgrade from an earlier version?  If an upgrade, from what?  windows 8 and newer use UEFI, did you install Ubuntu UEFI?  The link you posted explains installing Ubuntu if you are using the older MBR method.  Resizing or modifying partitions on windows should work from Ubuntu but you are generally better off modifying a windows system with it's software.  More details on your setup will be needed.  The best way to get that is to boot the Ubuntu installation medium and go to the site below where you can download boot repair software.  When you run it, select the option to Create Bootinfo Summary and post that output here and someone should be able to help.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by oldfred on 2015-09-30
Best to always resize NTFS partitions with Windows and reboot immediately into Windows so it can run chkdsk. The chkdsk is always required after a size change.
Do you have good backups of Windows and a repair flash drive or installer to fix Windows issues?

Is Windows UEFI & did you install Ubuntu in UEFI boot mode?
What brand/model system? What video card/chip?
Best to see details, post link to Summary Report.
       [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by onetome on 2015-09-30
> **yancek said:**
> and post that output here and someone should be able to help.

Here's my bootinfo, stored [here]("http://paste.ubuntu.com/12627931/").

Sorry for not pasting here. Its a long sucker -- 1000+ lines. Hah.

If you can read my bootinfo, bless you.

As for my computer... its an

[LIST]
[*]Acer Aspire V5
[*]Intel i7-4712MQ processor
[*]16 GB RAM
[*]64-bits (obviously)
[*]Windows 10, upgraded from 8.1, which was upgraded from 8.
[*]1 TB HDD
[*]Purchased a year ago
[/LIST]

Of which information is probably in the bootinfo paste dump.

And yes, I installed Ubuntu in UEFI, like the instructions (first post) instructed.

I do have a USB stick that was created in case everything explodes. Its a Windows 10 recovery USB, or something.

Thank you.

---

### Post by onetome on 2015-09-30
Its a dual graphics card -- some Intel card and a dedicated Nvidia GeForce GT 750M.

---

### Post by ubfan1 on 2015-09-30
Try selecting the "ubuntu" choice in the EFI menu (some function key like f12 at power-on).  That should get you to the grub menu.  You might have video issues with the Nvidia card, so the "nomodeset" word might need to be added to the grub line starting with "linux".  At the grub menu screen, type "e" to edit (instructions at bottom of screen) and add "nomodeset", replacing the "quiet splash" on that line.  If that works, search this forum for "Nvidia" to see about adding the proprietary drivers.

---

### Post by oldfred on 2015-09-30
Acer is the one that requires a supervisor password and you have to drill down to the ubuntu .efi files and set "trust" on them. Then it should boot but you will need the nomodeset ubfan1 discusses above for nVidia. Then install nVidia driver.

       Video on getting into UEFI - 1 Min Acer but similar to all Windows 8
[http://www.youtube.com/watch?v=QGiG1oljjZI](http://www.youtube.com/watch?v=QGiG1oljjZI)
            Acer Aspire ES1-512-C39M Details on supervisor password and settings to enable trust on ubuntu entries Also R14 model same fix
One of several with more details:
[http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[http://ubuntuforums.org/showthread.php?t=2291335](http://ubuntuforums.org/showthread.php?t=2291335)
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)
[http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)
[http://acer.custhelp.com/app/answers/detail/a_id/29349/](http://acer.custhelp.com/app/answers/detail/a_id/29349/)
[http://ubuntuforums.org/showthread.php?t=2290594](http://ubuntuforums.org/showthread.php?t=2290594)
Details on password & trust setting:
[http://askubuntu.com/questions/597213/bootable-device-not-found-after-clean-install-of-ubuntu-14-04-uefi](http://askubuntu.com/questions/597213/bootable-device-not-found-after-clean-install-of-ubuntu-14-04-uefi)
[http://askubuntu.com/questions/597213/bootable-device-not-found-after-clean-install-of-ubuntu-14-04-uefi/653202#653202](http://askubuntu.com/questions/597213/bootable-device-not-found-after-clean-install-of-ubuntu-14-04-uefi/653202#653202)
How to install Ubuntu for dual-boot with Windows 8 on Acer Aspire V5-551G. Post #3 Supervisory password required
[http://ubuntuforums.org/showthread.php?t=2176273](http://ubuntuforums.org/showthread.php?t=2176273)

---

### Post by onetome on 2015-10-01
I discovered how to boot. Its Start > Right Click > Shut Down or Sign Out > Restart + Shift Key > Other Devices > ubuntu.

As for trusting and nomodeset ubfan1, will look into that.

Thank you for the input. :)

---

