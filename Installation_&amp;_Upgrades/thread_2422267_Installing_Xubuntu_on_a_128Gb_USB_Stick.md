---
title: "Installing Xubuntu on a 128Gb USB Stick"
date: 2019-07-04
forum: Installation &amp; Upgrades
---

### Post by marc17 on 2019-07-04
Hi,

I was installing xubuntu on a USB 3.1 Drive. I tested it with BIOS and UEFi installations, but it seams that I can't boot it on every PC/MAC later on.

I often get boot errors, so it will not boot at all. Now I saw some small guides on how to install in BIOS mode and later add the UEFi on the Stick. (with a previously created UEFI partition) But the problem is that it is without the LUKS encryption. I want to use disk encrption in case I am loosing the USB stick with personal dokuments or pictures.(no I don't want to use Veracrypt:) and put them into an encrypted file)

If I am installing it from a PC without HD could I think it will have a problem booting later on if another HD is in the PC which is recognized first. Could this Boot Error result from a HD problem or is it the Bios/Uefi installation? Should I try to set up Grub with the UUID of the disk rather then with SDA?

I am new to linux and I don't want to give up MacOS or Windows yet, so I want a propper installed Linux that I can boot on my PC/MAC Systems and where I can learn Linux step by step. Virtual Box isn't a solution as my Laptop is quite slow with running MacOS an Linux in the box.

Thanks for your thoughts,

M.

---

### Post by C.S.Cameron on 2019-07-04
Full BIOS/UEFI install to USB that works for me.
[https://askubuntu.com/questions/1142544/standard-uses-of-usb-if-ubuntu-is-installed/1142675#1142675](https://askubuntu.com/questions/1142544/standard-uses-of-usb-if-ubuntu-is-installed/1142675#1142675)

---

### Post by oldfred on 2019-07-04
With UEFI grub default installs to first drive, usually the internal drive. So ESP on internal drive has boot files & external drive install has no bootable files.
Also with external drives all UEFI boots from /EFI/Boot/bootx64.efi, where internal drives boot from /EFI/ubuntu/shimx64.efi & additional files. Grub now does add a bootx64.efi, so that is less of an issue.
Both Windows & Ubuntu installers use /EFI/Boot/bootx64.efi as boot, but obviously different files.
See this bug for one work around:
        Ubuntu Installer uses wrong bootloader location for USB/sdb UEFI installs 
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1173457](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1173457)
Posted work around to manually unmount & mount correct ESP during install
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229488](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229488)
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1229488](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1229488)

Before work around during UEFI install to use correct ESP, we just copied /EFI/Boot & /EFI/ubuntu from internal drive to external drive. Both needed as Ubuntu's full install needed some of the files in /EFI/ubuntu where installer has everything in /EFI/Boot but is a limited version of grub/shiim just for installer.
 
I used to have both an ESP - efi system partition for UEFI boot and a bios_grub partition for BIOS boot on a gpt partitioned drive, so one flash drive could be both BIOS & UEFI. But they can get out of sync with updates, so I just use multiple flash drives. 

Be sure to partition in advance with gpt.
I do not use LVM nor encryption, so review this:
      
 [https://help.ubuntu.com/community/ManualFullSystemEncryption/](https://help.ubuntu.com/community/ManualFullSystemEncryption/)
Full-system encryption with manual control and dual-booting Paddy Landau
[https://ubuntuforums.org/showthread.php?t=2357627](https://ubuntuforums.org/showthread.php?t=2357627) & 
[https://ubuntuforums.org/showthread.php?t=2399092](https://ubuntuforums.org/showthread.php?t=2399092)

---

### Post by marc17 on 2019-07-04
Hi,

thanks alot for the information, I guess I have some reading to do this evening :)
thank you very much C.S.Cameron and oldfred 

M.

---

