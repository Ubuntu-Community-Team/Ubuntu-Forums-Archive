---
title: "How to install ubuntu 20.04 on non UEFI machine"
date: 2020-05-27
forum: Installation &amp; Upgrades
---

### Post by nocom2 on 2020-05-27
I try to install ubuntu 20.04 on my Acer Aspire V5 laptop containing windows 10 (upgraded from 7). My laptop has a non-uefi BIOS AFAIK. I cannot find any trace on UEFI or "legacy" in the BIOS and in a later stage boot-repair saves the day by copying the MBR back (more about that later). So I assume that it is a non-UEFI laptop.

The reason I elaborate on this is when I try to install ubuntu the installer warns that I should add an EFI partition else the installation may crash. I ignored that, the grub-installer warned that it could not be executed on /dev/sda and crashed. Rebooting brought me into a basic GRUB> prompt that could not boot. I tried again by first creating an EFI partion of 855MiB but that had the same result. Boot repair was not able to make something out of this, its report is on [pastebin]("http://paste.ubuntu.com/p/qbv5PXCY73"). Fortunately boot-repair was able to restore the MBR and with that my old situation.

My questions: can I install Ubuntu 20.04 on this laptop and if so, is there some link where on how to do that? Searches to installing ubuntu on non_UEFI systems yielded just links to installing on UEFI systems :(.

---

### Post by CelticWarrior on 2020-05-27
Regardless of the firmware, BIOS or UEFI, the installer always installs in the same mode it was booted. So, if you were able to boot in UEFI mode, you have UEFI, not BIOS. But surely Windows is in BIOS/Legacy mode and Ubuntu should be installed in that mode as well in order to have a working dual-boot with Grub.

Windows 7 was typically installed in BIOS/Legacy mode even in early UEFI machines and despite the fact that Windows 7 supports UEFI mode. Consequently the upgraded Windows 10 is also in BIOS/Legacy. So, either reinstall Windows and Ubuntu in UEFI mode or assure you're booting the Ubuntu installer in Legacy mode. You should see two entries for the USB device, one with "UEFI:" and other without it.

---

### Post by ajgreeny on 2020-05-27
See **Boot-Repair** in my signature below and follow the instructions there to run the Boot-Info-Script.	 

**Do not run the default repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system.

---

### Post by CelticWarrior on 2020-05-27
@ajgreeny

Already in the OP: [https://paste.ubuntu.com/p/qbv5PXCY73/](https://paste.ubuntu.com/p/qbv5PXCY73/)

---

### Post by nocom2 on 2020-05-27
The options I get are:    - Ubuntu  - Ubuntu (Safe Graphics)    - OEM install     - Boot from next volume    - UEFI firmware settings    Ubuntu graphics is same as ubuntu   OEM i didn't try   Boot next volume ends in a reboot   UEFI firmware I get the error: error: can't find command fwsetup.     Maybe It is an UEFU laptop, but why does the installer warn for not having an EFI partition and after installation the grub-installer crashes and why happens the same thing when I create an EFI partition?

---

### Post by CelticWarrior on 2020-05-27
Again, hoe it boots is how it install. And because you see "UEFI firmware settings" you're clearly booting in UEFI mode.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

This shows the difference between the initial Grub menu when booting a live session. 
Again, without major changes - reinstallation of Windows in UEFI mode - you need to assure you're booting the Ubuntu USB in Legacy mode, the same as your current Windows.

---

### Post by ubfan1 on 2020-05-27
I have an old Lenovo which a BIOS/UEFI firmware setting allows you to set a preference which mode, UEFI or legacy, boots when both are present.  Look for such a setting and set it to "legacy before UEFI".

---

### Post by nocom2 on 2020-05-27
Thanks for all your help! I   made it, but don 't ask me how.    And sorry my previous mail was so terribly messed up. I had some bad experiences with legacy/UEFI in the past so that made me quite aware of the issue. I kn ow the settings for that in my PC, but really, there is no such settings in my Acer Aspecite V5 laptop. The BIO is extremely simple, when I skip over the Boot and Exit menu options their are exactly nine (9) options and none of it even borders on legacy or UEFI. I next did not want to mess up with my windows setup. Upgrade from windows 7, no CD anymore so that was what I really did not want to touch. CelticWarrior made my day telling me this was an UEFI laptop so it really had to be something during the install. I used the same UIbuntu iso, but this time I used BalenaEtcher to create the USB stick. This yielded other options during boot, I chose another one (third one, forgot how it was called) . This passed thru  Grub install. Thanks guys!

---

### Post by oldfred on 2020-05-27
Two other V5 installs.
How to install Ubuntu for dual-boot with Windows 8 on Acer Aspire V5-551G. Post #3 Supervisory password required
[http://ubuntuforums.org/showthread.php?t=2176273](http://ubuntuforums.org/showthread.php?t=2176273)
Acer V5-571P-6815 secure boot off worked Shows Diskpart
[http://ubuntuforums.org/showthread.php?t=2081311](http://ubuntuforums.org/showthread.php?t=2081311)

---

### Post by GhX6GZMB on 2020-05-27
Just for general info: 20.04 will install perfectly on BIOS machines, no issues.
The first menu is "Start Ubuntu" - "Ubuntu (Safe Graphics)" - "Test Memory" - "Boot from first Hard Disk"

Choose first option and it just runs.

---

