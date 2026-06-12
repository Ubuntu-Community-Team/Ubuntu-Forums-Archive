---
title: "Grub and dual boot on 2 SSDs"
date: 2019-02-08
forum: Installation &amp; Upgrades
---

### Post by xndE3Dw on 2019-02-08
I currently have a Windows 10 PC (UEFI) and planning to add an Ubuntu install this weekend, on a separate SSD.

The original plan is to install Windows and Ubuntu on separate SSDs and use the boot menu F11 (rather than Grub) to boot into any of the OS when I want - an inconvinience I'm happy to bear because I really can't afford to not be able to boot into windows if I break Ubuntu or Grub.

However I'd like to ask if it's possible to install Grub only on the Ubuntu ssd such that nothing from Ubuntu/Grub is written to the windows ssd/bootloader, If I do this, will Grub still discover the Windows on the other disk and give me option to boot into it. This way if I ever break Ubuntu, I can just remove the Ubuntu ssd and then continue using Windows.  

Thanks.

---

### Post by oldfred on 2019-02-08
Ubuntu's version of grub is still  not fixed.
       Ubuntu Installer uses wrong bootloader location for USB/sdb UEFI installs 
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1173457](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1173457)
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229488](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229488)
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1229488](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1229488) 
    
I just installed 19.04 to my sdb drive, to see it that has been updated and it said it was installing to the sdb drive, but overwrote my default LTS boot on sda. I do not have Windows.
I do prefer that each drive have boot loader for install on that drive.

Often easier to just disconnect or turn off Windows drive in UEFI so not seen. Then install will only install to your Ubuntu drive. After install you can run sudo update-grub to add Windows to grub menu. But you must install Ubuntu in same boot mode, usually UEFI now, as grub only will boot other installs in same boot mode.

I partition sdb or any external drive first with gparted and include an ESP - efi system partition as first partition. Then copy /EFI/ubuntu to sdb drive. I do not reconfigure UEFI to use that, but add second install to my default grub entry on sda. Currently my ESP on sdb is just a backup of the ESP on sda, but could easily be reconfigured to be bootable. If you do not have ESP, then difficult to make bootable and default install will just use first ESP found, usually the Windows one.

If you disconnect a drive, UEFI usually forgets UEFI entries from that drive. But it seems most auto find Windows, but not Ubuntu. You then can use efibootmgr or reinstall grub (which uses efibootmgr) to readd Ubuntu entries if you disconnect a drive with Ubuntu.

More info on general UEFI install and section with links to other threads on two drive, or external drive/flash drive installs in link below in my signature.

---

### Post by xndE3Dw on 2019-02-08
That was helpful. Thanks

---

