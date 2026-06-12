---
title: "wubildr.mbr Missing?"
date: 2012-12-26
forum: Installation &amp; Upgrades
---

### Post by The Floating Brain on 2012-12-26
Hello all,
    I am having a bit of trouble getting Ubuntu 12.04 LTS to install on my new laptop (running Windows 7), I have done this procedure about five times before with little to no trouble however I can not figure out what is wrong this time. It looks like Windows Boot Loader can not find \ubuntu\winboot\wubildr.mbr, the exact error message is: "The selected entry could not be located the application is missing or corrupt". I have tried this twice (once on my C: drive once on my flash drive). Any help is appreciated!

P.s I am a programmer, so you do not have to beat around the bush :-)

P.s.s I would like to get this running on my flash drive :-D (16 Gigs)

---

### Post by oldfred on 2012-12-26
Welcome to the forums.

I am not real knowledgeable on wubi, but only one or two here in the forum really are.

You mention new computer but Windows 7. Some new Windows 7 systems are using UEFI to boot, similar to Windows 8, but without secure boot. If Windows is booting with UEFI, you then have gpt partitions and wubi does not yet work with gpt partitions. 

       [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

       HOW TO Avoid Wubi & Install Ubuntu on USB Drive -
[http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)

With a large flash drive I prefer a full install.
Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

But if you only have Windows I am not sure how to install anything other than the USB installer which then can have persistence.
       [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by The Floating Brain on 2012-12-27
Thank you for the detailed reply!

Darn, I specifically got Windows 7 so I would not have UEFI :-( , that stinks. The methods you mentioned, will they all work even if I have UEFI?

---

### Post by oldfred on 2012-12-27
Do you have UEFI or BIOS based install? However Windows is installed is how Ubuntu must be installed. If Windows 7 and UEFI you do avoid all the issues of secure boot.

If partitions are gpt not MBR(msdos) and first partition is efi then you have UEFI. If msdos and first partition is just a 100MB boot/repair Windows boot partition then you have BIOS based install. 
Most newer systems are UEFI, but still may use BIOS (CSM) mode.

From terminal in live installer, DVD or flash drive, post inside code tags to preserve formatting (# in edit panel):

       sudo parted /dev/sda unit s print

---

