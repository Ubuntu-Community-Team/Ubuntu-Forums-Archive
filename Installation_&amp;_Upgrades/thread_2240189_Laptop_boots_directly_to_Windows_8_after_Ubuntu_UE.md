---
title: "Laptop boots directly to Windows 8 after Ubuntu UEFI install alongside"
date: 2014-08-18
forum: Installation &amp; Upgrades
---

### Post by stavros3 on 2014-08-18
Hello,
I have read many guides about how to dual boot windows 8 and ubuntu and have installed ubuntu more than 10 times the past three days but I can't get to load the grub menu.
I have a toshiba satellite laptop C55-A-1NK and windows 8 installed in a 300GB/750GB partition. The steps I followed are the following:
1. Make a  ubuntu 14.01 live usb using rufus on windows 8, selecting GPT and fat32 so it is uefi bootable.
2. Turn off fast boot, secure boot. 
3. Booting with the live usb (uefi mode)
4. Installing Ubuntu in a 380GB partition, making some swap space.

After the installation  I cant get to load the grub menu. I tried using boot repair and this is what I get:
[http://paste.ubuntu.com/8081052/](http://paste.ubuntu.com/8081052/)
I know there are many similar posts , but I have read many of them and I cant solve my problem.

---

### Post by bizhat on 2014-08-18
Install EasyBCD from

[https://neosmart.net/EasyBCD/](https://neosmart.net/EasyBCD/)

Run it as Admin, it can scan for OS and add it to your boot menu.

---

### Post by yancek on 2014-08-18
You have nothing in the mbr which would be correct for uefi.  A UEFI/GPT install usus a vfat partition where it puts the EFI files which is probably sda2 in your case.  I don't see the files one would expect to see for windows or Ubuntu.  Are you able to boot windows?  I don't use UEFI so you'll need to wait for help from someone else.

---

### Post by oldfred on 2014-08-18
Do not use EasyBCD with UEFI, not required.

It does show standard Windows UEFI partitions and gpt partitioning. And Windows only boots with UEFI on a gpt partitioned drive. 
But script did not show any of the files normally in the efi or FAT32 partition. The os-prober did see the Windows efi files as it added a boot for Windows to the grub menu.
 Found Windows Boot Manager on /[EMAIL="dev/sda2@/EFI/Microsoft/Boot/bootmgfw.efi"]dev/sda2@/EFI/Microsoft/Boot/bootmgfw.efi[/EMAIL]

Do you have these folders with files in them in sda2?
 /EFI/Boot
/EFI/Microsoft/Boot
/EFI/ubuntu

Can you use one time boot key, often f12 but varies by vendor to choose what system to boot?
Or from UEFI choose the ubuntu entry?

BootOrder: 0003,0000,2003,2001,2002
Boot0000* Windows Boot Manager
Boot0001* UEFI: Network Card
Boot0002* UEFI: Network Card
Boot0007* UEFI: Lexar USB Flash Drive 1100
Boot2001* EFI USB Device
Boot2002* EFI DVD/CDROM
Boot2003* EFI Network
Boot0003* [COLOR=#ff0000]ubuntu[/COLOR].

It does say ubuntu is first in boot order.
Also have you tried with both secure boot on and secure boot off?

---

### Post by stavros3 on 2014-08-19
OK I have the folders you asked for in sda2:
/EFI/Boot
/EFI/Microsoft/Boot
/EFI/ubuntu

/EFI/Boot : **bootx64.efi**
/EFI/Microsoft/Boot: Boot/.**. many files here**
/EFI/Ubuntu: grub.cfg/
[B] shimx64.efi
 grubx64.efi
 MokManager.efi
grub.cfg[/B]

My BIOS doesnt have the option to select partitions, you can only select devices so  I cant choose Ubuntu. I think I have tried installing with secure boot on, and it failed. Should I try again? Booting with secure boot On now however still loads windows 8.

Thanks for your answers

---

### Post by oldfred on 2014-08-19
Be very careful if you reinstall. Only use Something Else to manually chose existing partitions.
The auto install over "Ubuntu" actually should say erase entire drive, but does not:
       Reinstall says overwrite Ubuntu but it also erases existing Windows.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

Often then if you have only devices, somewhere else even on another page, or under a title with a > will be the logical boot options which should include both Windows & ubuntu.
One time boot key normally includes both.

If you select the hard drive when in UEFI mode that should boot the bootx64.efi file.
One of the common work arounds is to copy grub or shim into the /efi/Boot folder and rename grub to bootx64.efi. Then set hard drive as first in boot order.

Backup efi partition first. 
And maybe rename bootx64.efi so you have the copy.

 sudo mount -t vfat /dev/sda2 /mnt
sudo cp /mnt/EFI/ubuntu/grubx64.efi /mnt/EFI/Boot/bootx64.efi


That overwrites the bootx64.efi with grub, so booting hard drive should load grub menu.

Other work arounds:
       [http://askubuntu.com/questions/507013/windows-8-1-changes-boot-order](http://askubuntu.com/questions/507013/windows-8-1-changes-boot-order)
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
[http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)

---

