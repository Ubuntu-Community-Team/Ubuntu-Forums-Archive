---
title: "Adjust Grub settings such that right kernel is loaded"
date: 2015-07-18
forum: Installation &amp; Upgrades
---

### Post by steffen8 on 2015-07-18
Hello,

I have an old MacBook where I installed Debian a few weeks ago on a new SSD-drive. As I wanted to use the old hard-drive where I had a former Arch installation on top I bought one of these holders with which you can mount the old drive instead of the CDROM-drive. Now it seems that the hard-drives are recognized in a different order and I cannot boot directly anymmore, as I also deleted the Arch /boot and /swap partitions. What I have been doing the past days was using a Ubuntu LiveCD to get Grub and then fire up my Debian system with 
```

linux (hd1,gpt2)/vmlinuz....
initrd (hd1,gpt2)/initrd...
boot

```
But jeah, I am growing tired of this solution and I am looking for a way to directly fire up my installation from sda. I used boot-info to gather some information: [http://paste.ubuntu.com/11898514/](http://paste.ubuntu.com/11898514/). Can I just update my grub.cfg or what would be the right way of going about it? Actually does someone know why this problem actually ocurred? 

Thank you a lot in advance,
Steffen

---

### Post by oldfred on 2015-07-18
I do not know Mac nor Encryption.

But what I have read was that is was usually better to boot a Mac with UEFI, not BIOS. You should both a grub in MBR and an efi partition. And UEFI with only the hard drive default or fallback boot of bootx64.efi.

You also have hybrid partitioning.
 [http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html)
Normally hybrid is only required on Mac as Mac boots with UEFI, but Windows only booted with BIOS from MBR. Not sure if newer Windows with UEFI even still boot with Mac's old UEFI.
But you then have to keep partitions in sync.
But with Ubuntu you do not need hybrid. Ubuntu will boot in BIOS or UEFI boot mode from gpt partitioned drive. Probably better to undo hybrid and just have gpt.
Ubuntu does need 1 or 2MB unformatted partition with bios_grub flag to boot in BIOS mode. Otherwise grub will not install correctly. Or you need the efi partition for UEFI boot.

If booting Ubuntu from live installer, then you probably are booting in UEFI mode as once you start to boot in one mode you cannot change to BIOS unless you totally reboot.

> BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.


Some old threads I saved, not sure how useful.
 [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx)
[http://askubuntu.com/questions/580202/refit-refind-grub2-what-is-the-right-way-for-ubuntu-14-10-on-a-mac](http://askubuntu.com/questions/580202/refit-refind-grub2-what-is-the-right-way-for-ubuntu-14-10-on-a-mac)
[https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)
Bugs Ubuntu fails to properly boot on Macbook Air 2013 6,1 & 6,2 - Use UEFI not CSM
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1197451](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1197451)
Post #6 booting Kubuntu 12.10 in EFI mode on my Mac, by  trogdor1138
Boot Ubuntu from efi with Mac trogdor1138
[http://ubuntuforums.org/showthread.php?t=2091257](http://ubuntuforums.org/showthread.php?t=2091257)
 MacBook Pro 8,2: howto for dual boot Ubuntu/MacOS EFI with rEFInd
[http://ubuntuforums.org/showthread.php?t=2157775](http://ubuntuforums.org/showthread.php?t=2157775)
Bit older, Mac & PC UEFI, note issues on some systems
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)
[http://www.rodsbooks.com/ubuntu-efi/index.html](http://www.rodsbooks.com/ubuntu-efi/index.html)

---

