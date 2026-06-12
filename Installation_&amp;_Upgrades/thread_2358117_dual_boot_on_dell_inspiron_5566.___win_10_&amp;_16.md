---
title: "dual boot on dell inspiron 5566.   win 10 &amp; 16.04"
date: 2017-04-09
forum: Installation &amp; Upgrades
---

### Post by mackaframa85 on 2017-04-09
can any body point me to any solid documentation to do a dual boot install with windows 10.   I've seen guides that modify the efi partition with the windows boot loader files and Im not sure about this.  Ive seen other guides where it specifies install alongside windows 7 boot manager.  At this point I'm a little confused and dont want to end up erasing my windows efi boot.

---

### Post by yancek on 2017-04-09
There are differences between windows 10 and windows 7 when they are pre-installed.  windows 7 is usually an MBR install while the default for windows 8 and 10 is to use UEFI.  If you are using GPT  partitioning, then with windows you need to use UEFI.  Dual booting windows 10/Ubuntu UEFI is explained at the site below which is the official Ubuntu documentation.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by mackaframa85 on 2017-04-09
I know I need to make a free space partition to install ubuntu using windows first.  My main issue is do I just choose the first option in the installer or choose something else.  Create ext 4 filesystem mounted as root - but if you do the manual install where should the boot loader go?   Would ubuntu just recognize the free space and install grub in place of the windows boot loader if I choose the first option.  I think its either grub or Windows boot loader.  I dont remember booting up dual configuration where grub didnt pop up

---

### Post by Dennis N on 2017-04-10
Ubuntu with UEFI always installs the boot loader on your first sata disk - sda - regardless of the installation method. There is a setting for boot loader location on the partitioning screen, but it does not work for UEFI, so just leave it set to sda.

It will also install some boot files in the existing EFI system partition that Windows uses, but these will not interfere with Windows files. 

When done and rebooted, the system should boot to Ubuntu grub menu on startup.

Added note:

In the guide at:

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

I believe there probably is a mistake in "General Princlples" 6-2: "if you use the manual partitioning ("Something else"), the difference is that you will have to set the /boot/efi mount point to the UEFI partition."

As I recall, I don't think you can choose which partition to mount at /boot/efi. There just is no option for that in the Ubuntu installer.

You can check on this when you install.

---

