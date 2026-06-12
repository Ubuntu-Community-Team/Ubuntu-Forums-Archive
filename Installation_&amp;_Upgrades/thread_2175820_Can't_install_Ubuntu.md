---
title: "Can't install Ubuntu"
date: 2013-09-21
forum: Installation &amp; Upgrades
---

### Post by tomas4 on 2013-09-21
Hi,

I cant install Ubuntu. After following all the steps here: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)   I still cant install Ubuntu properly.

I have done the step 5: "If the PC does not load Ubuntu (but instead loads Windows, for example, as in [Bug #1050940]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1050940")), or if the Windows entry in the [GRUB 2]("https://help.ubuntu.com/community/Grub2") menu does not boot Windows (see [Bug #1024383]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383")), boot your PC using the Live CD/DVD or Live USB and choose "Try Ubuntu" once again. When the live session has loaded, run [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair") (see link for details). When Boot-Repair loads, click on the "Recommended repair" button, and write on a paper the URL (**paste.ubuntu.com/XXXXXX/**) that will appear. Then reboot the pc."

I still cant load Ubuntu.

I got this url: [http://paste.ubuntu.com/6136506/](http://paste.ubuntu.com/6136506/)


Thank you for your help

---

### Post by mikewhatever on 2013-09-21
It looks like you've been trying to do a Wubi install, which is known to not work well with Windows 8 and UEFI.
[https://wiki.ubuntu.com/RaringRingtail/ReleaseNotes#Ubuntu_downloader_for_Windows_discontinued](https://wiki.ubuntu.com/RaringRingtail/ReleaseNotes#Ubuntu_downloader_for_Windows_discontinued)

I'd suggest you try a supported installation mode, for example in a VM, or get another HDD and install to that.

---

