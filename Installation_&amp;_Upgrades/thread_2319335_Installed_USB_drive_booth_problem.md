---
title: "Installed USB drive booth problem"
date: 2016-04-03
forum: Installation &amp; Upgrades
---

### Post by joshuayip on 2016-04-03
Hi guys, 

New to this forum and a noob in linux. Was playing with mint, but I can never get it installed into a usb like ubuntu. Installed - not a live usb. So I tried to install an ubuntu into a usb:

Here is my prb:

1. I used an unbranded 4gb(corp gift) live ubuntu usb (14.04 if not wrong) and installed it into a 32 gb sandisk on a thinkpad L430 laptop running windows 7
2. removed 4gb usb, and 32gb installed ubuntu boot up without any issue

here is the prb
1. my windows no longer boot - the installation processed changed my bios. All the stuff in the bios (Boot Priority Order) only shows 1 item - ubuntu. The rest (USB FDD, HDD, CD ROM) . 
2. out of desperation - I hit "restore default config" in the bios and all the items in "Boot Priority Order" returned. 
3.  Here is the issue --> my ubuntu no longer boots up after I plug it in. . 

Here is the boot-repair information. I dare not execute the repair , as I really have no idea what it will screw up 

[http://paste.ubuntu.com/15597032/](http://paste.ubuntu.com/15597032/)

Appreciate some advice how to make the installed ubuntu usb boot.

---

### Post by sudodus on 2016-04-03
Welcome to the Ubuntu Forums :-)

I think that you installed the bootloader into the internal drive.

This works in BIOS mode:

The best method to avoid that is to remove the internal drive, and then install Ubuntu into the USB drive. The second best method (more risky, but also more convenient) is to select ***Something else*** at the partitioning window of the installer.

Then you have to [create and] select the partitions manually, and at the bottom of the window, you will be able to select where to install the bootloader. Write it to the head of the USB drive, **/dev/sdx**, for example /dev/sd**b**. Do ***not*** use any digit (not /dev/sdb1) - which means that you write it to a partition, and that is not what you want.

If your computer is running in UEFI mode, things are more complicated. You can try according to the following method, iIf you want a pendrive with a live **and** an installed system, that works in UEFI and BIOS mode,

[A new and so far successful attempt to create a stable portable system, that works in UEFI and BIOS mode]("http://ubuntuforums.org/showthread.php?t=2213631&p=13262506#post13262506")

-0-

It is also possible to repair or re-install the grub boot-loader for linux according to the following link

[Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

and there are corresponding tools to re-install the Windows bootloader.

---

### Post by yancek on 2016-04-03
Your problem is that you have mixed an MBR install with a UEFI install and the results expected are what you have.  You need to install both/all systems either using UEFI or both/all using MBR on the same computer.  I also notice you have LiLo code in the MBR of your first disk (sda) which is Linux Loader.  I don't know where that came from as I don't believe Ubuntu ever used it, at least hasn't for years if ever.

Probably the simplest solution to this problem is to reinstall Ubuntu to the 32GB flash drive and this time install using MBR and when you do, install the Grub bootloader to the MBR of sdc, the flash drive.  I expect that you will need to reinstall windows boot code to the MBR of sda with the windows installation DVD or you will likely not be able to boot windows without your Ubuntu flash drive attached..

---

### Post by oldfred on 2016-04-03
I have often suggested the lilo boot loader as a open source Windows boot loader, but you had to manually install that.
Boot-Repair installs the syslinux boot loader for booting Windows.
Both are for BIOS boot on MBR partitioned drives.

While you can boot Windows in BIOS mode, and Ubuntu in UEFI mode, you can only do that from UEFI boot menu. And some systems require you to turn on/off UEFI or CSM/BIOS/Legacy boot settings.
As yancek suggests best to have all systems in same boot mode, either UEFI or all BIOS.

You can convert a UEFI Ubuntu install on gpt partitioned drive to BIOS boot.
You need to first add anywhere on drive a tiny 1 or 2MB unformatted partition with the bios_grub flag if using gparted.
Then run Boot-Repair's advanced mode to install grub-pc(BIOS) and un-install grub-efi-amd64(UEFI).
Be sure to install grub to sdc or Ubuntu drive, not the typical default of sda.

---

