---
title: "[SOLVED] Install packages from liveusb to installed disk"
date: 2017-08-28
forum: Installation &amp; Upgrades
---

### Post by exadmasta on 2017-08-28
Hello, I installed lubuntu 17.04 with encrypted lvm and it seems to have a bug. lack of lvm2 package is causing me to be unable to boot after installation. 

Is there a way to install the lvm2 package to my installed disk from the liveusb? The volume is encrypted so I'm not sure if I'd be able to mount the encrypted volume and chroot in? Sorry for my noobiness.  Any help is appreciated. Would it be easier to try and install an older version of lubuntu with encrypted lvm and then upgrade?

---

### Post by oldfred on 2017-08-28
I do not know LVM nor encryption.
But may be better for those that do, to see the details.

 May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/) 


If you installed in LVM mode, it just about has to have lmv2. Grub may also have an lvm driver - insmod lvm.

While this is about resizing, the first part is mounting your LVM partition and then you can do other maintenance.
 How to: Mount & Resize an Encrypted Partition (LUKS) also mount for repairs
[http://ubuntuforums.org/showthread.php?p=4530641](http://ubuntuforums.org/showthread.php?p=4530641)
sudo apt-get update && sudo apt-get install lvm2 cryptsetup

---

### Post by exadmasta on 2017-08-28
> **oldfred said:**
> I do not know LVM nor encryption.
But may be better for those that do, to see the details.

 May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/) 


If you installed in LVM mode, it just about has to have lmv2. Grub may also have an lvm driver - insmod lvm.

While this is about resizing, the first part is mounting your LVM partition and then you can do other maintenance.
 How to: Mount & Resize an Encrypted Partition (LUKS) also mount for repairs
[http://ubuntuforums.org/showthread.php?p=4530641](http://ubuntuforums.org/showthread.php?p=4530641)
sudo apt-get update && sudo apt-get install lvm2 cryptsetup

Ah sorry, should have mentioned it's a known bug with the version I used. I had to install lvm2 within the liveusb just to get lubuntu 17.04 to install with encryption. when I boot to the os after install it put me in BusyBox prompt apparently the fix is to try and boot with an older kernel though I didn't have an older kernel selectable in grubs boot options or install lvm2 but I couldn't get into the installed os to do either of those.. In any case, it'll just be easier to use an older or alternative installer with encryption working properly then to try and fix the existing install. Thanks for the help though.

---

