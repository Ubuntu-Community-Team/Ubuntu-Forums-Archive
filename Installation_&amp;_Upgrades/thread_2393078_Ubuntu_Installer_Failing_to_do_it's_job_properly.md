---
title: "Ubuntu Installer Failing to do it's job properly"
date: 2018-05-29
forum: Installation &amp; Upgrades
---

### Post by falloutboy2 on 2018-05-29
So I started out with two identical 32GB USB 3 memory sticks, on both of them I placed Ubuntu 18.04 LTS using Rufus to write the image in ISO mode, booting onto either stick works in live mode.

I used Rufus to write both sticks to deliberately ensure they had an EFI bootable FS on them.

I then started through the installation process, I had one stick as /dev/hdc which was the source and /dev/hdd was the target.

I told the installer after partitioning /dev/hdd to put the boot load on /dev/hdd with the drop box provided - cool all done I thought.

5 Mins later it said it had finished, rebooted the system removed /dev/hdc went in through bios and selected the  USB disk to boot from.

Screen goes black, wait wait wait back into bios, me scratching my head.

Let Post complete to boot into windows after removing /dev/hdd  usb stick and low and behold what pops up GRUB on my PCIe X4 SSD specifically where I DID NOT WANT IT.

It had an option to boot into windows so I took it, the drive that I created with the install option from the linux desktop - unreadable, unbootable.

Now either every piece of documentation I have read that tells me how to create a bootable USB Ubuntu installation is wrong, or has something missing in each and every case or the installer stuffed up - which is it?

---

### Post by ubfan1 on 2018-05-29
It's UEFI. Take a look at bug 1173457.  Just copy all the hard disk's EFI files to the USB's (empty)  EFI partition.  Then it should boot when you select it.  You should be able to reorder the boot order to put Windows before  grub, then things should be working again.  The (unwanted) grub that got added to the hard disk is in .../EFI/ubuntu, and maybe .../EFI/Boot had the windows bootloader bootx64.efi renamed and a grub64.efi or shim64.efi put in its place.  If you can boot Windows, don't worry about it.

---

### Post by oldfred on 2018-05-29
Full link to bug, please add to it.
 Ubuntu Installer uses wrong bootloader location for USB UEFI installs 
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1173457](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1173457)
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229488](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229488)

---

### Post by falloutboy2 on 2018-05-29
> **ubfan1 said:**
> It's UEFI. Take a look at bug 1173457.  Just copy all the hard disk's EFI files to the USB's (empty)  EFI partition.  Then it should boot when you select it.  You should be able to reorder the boot order to put Windows before  grub, then things should be working again.  The (unwanted) grub that got added to the hard disk is in .../EFI/ubuntu, and maybe .../EFI/Boot had the windows bootloader bootx64.efi renamed and a grub64.efi or shim64.efi put in its place.  If you can boot Windows, don't worry about it.

The only problem with not worrying about it is it doesn't achieve what i need, I need a USB stick which is independently boot-able on multiple machines and alterable for network testing. And the fact that it touched my PCIe x4 SSD without permission - that really annoyed me.

---

### Post by falloutboy2 on 2018-05-30
Well that is it for me, after mucking around with something that should just work for two days, manually copying files and getting grub to try and do it's job - I give up - it's far to difficult to get this thing up and running - something that should have been a simple task has just been a massive waste of time.

I started this to test two network cards before returning them to have them checked out to make sure the issues being caused wern't specific to windows - but it's way to much effort.

Fix the damned installer.

---

### Post by falloutboy2 on 2018-05-30
> **falloutboy2 said:**
> Well that is it for me, after mucking around with something that should just work for two days, manually copying files and getting grub to try and do it's job - I give up - it's far to difficult to get this thing up and running - something that should have been a simple task has just been a massive waste of time.

I started this to test two network cards before returning them to have them checked out to make sure the issues being caused wern't specific to windows - but it's way to much effort.

Fix the damned installer.

Well I finally sorted it out for it.

Using some of the details found on the following website which NO ONE else mentions when it comes to making a full USB bootable version of Ubuntu from a live USB key version I got the damned useless thing to work.

[URL="https://www.dionysopoulos.me/253-portable-ubuntu-on-usb-hdd.html"]https://www.dionysopoulos.me/253-portable-ubuntu-on-usb-hdd.html
[/URL]
Specifically you do the following

1. Ensure that Secure Boot and CSM are DISABLED in bios - not mentioned on any of the websites regarding turning Ubuntu into a self maintained USB.

2. Boot onto the USB Live version - in my case /dev/sdc

3. Open a terminal window and run
sudo gparted

4. Go through the list of drives and find the destination you want to put ubuntu onto - in my case SDD

Setup two partitions one extended taking the bulk of the space as an EXT4 partition the 2nd a smaller partition - I left mine at 4G and flag the second partition as ESP, Boot.

5. Exit gparted writing changes, close the terminal session and restart the system from the menu.

6. After the system is booted from the live USB key repeat step 4, Check the flags are correct and that the big partition shows EXT4, don't worry that the esp partition does not have a type

7 Exit gparted - don't write changes you don't need to and could cause the drive to be in use message forcing you to have to reboot again.

8. Go through the installation process as normal

9. When you hit the partitioning screen make sure you select the boot device without any numbers in the drop down box at the bottom.

10. Wait for install to finish and restart the system, I used F8 on startup to select the USB key to boot from and low and behold on startup I was the admin and everything was all go.

*** Tell the developers to fix this damned bug ***

---

### Post by QIII on 2018-05-30
We don't have any more say with the developers than you do.  We are all end-users just like you.

---

