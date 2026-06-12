---
title: "partition plan"
date: 2012-11-14
forum: Installation &amp; Upgrades
---

### Post by AstroLlama on 2012-11-14
Hi everybody, i'm back in the Ubuntu-realm after a few years of being away. Good to be back [a single tear runs down my cheek]. 

A lot has changed, it seems and I've been reading up on UEFI, secure boot, Ubuntu 12.10. I bought an ASUS A56C laptop preinstalled with Windows 8, it'd like to dual boot with Ubuntu Studio.

From what I've read it's best to shrink partitions in the windows disk management tool, restart windows, and then install Ubuntu to the empty space. My question is can I safely delete the D: partition (named "Data") or is it necessary for windows to run?
I don't think it is because the C: partition called OS seems to have all the windows system files. I have no data on partition D, it's just taking up space. I'm aware that this is technically a windows-question. I just wanted to make 100% sure.

My second question: is it correct that as windows 8 was preinstalled in UEFI mode that ubuntu should also be installed in UEFI mode?

What about secure boot? should that be disabled or does it not really make a difference?

---

### Post by pkadeel on 2012-11-14
> **AstroLlama said:**
> Hi everybody, i'm back in the Ubuntu-realm after a few years of being away. Good to be back [a single tear runs down my cheek]. 

A lot has changed, it seems and I've been reading up on UEFI, secure boot, Ubuntu 12.10. I bought an ASUS A56C laptop preinstalled with Windows 8, it'd like to dual boot with Ubuntu Studio.

From what I've read it's best to shrink partitions in the windows disk management tool, restart windows, and then install Ubuntu to the empty space. My question is can I safely delete the D: partition (named "Data") or is it necessary for windows to run?
I don't think it is because the C: partition called OS seems to have all the windows system files. I have no data on partition D, it's just taking up space. I'm aware that this is technically a windows-question. I just wanted to make 100% sure.

My second question: is it correct that as windows 8 was preinstalled in UEFI mode that ubuntu should also be installed in UEFI mode?

What about secure boot? should that be disabled or does it not really make a difference?
As long as you are in windows, if a partition contains system files, it won't let you do that silently. So if you are going to delete D: do it from within windows.

Windows has a tendency to keep hidden backup files and/setup installers on other partitions so make sure the partition is really empty before deleting it.

---

### Post by Mark Phelps on 2012-11-14
It's never "safe" to remove ANY partitions that are already present on a preinstalled Windows PC -- without first confirming two things:
1) What is IN the partition
2) You don't need the stuff in that partition

My guess, without seeing the PC, is that "D" is a Recovery partition, containing a compressed Windows image file, that could be used to restore your PC to its original state (know as a factory reset).

Win8 has some kind of "refresh" option in its new boot manager.  It probably uses the contents of this partition for that to work.  If you remove this partition, that's probably NOT going to work.

---

### Post by AstroLlama on 2012-11-14
> **Mark Phelps said:**
> It's never "safe" to remove ANY partitions that are already present on a preinstalled Windows PC -- without first confirming two things:
1) What is IN the partition
2) You don't need the stuff in that partition

My guess, without seeing the PC, is that "D" is a Recovery partition, containing a compressed Windows image file, that could be used to restore your PC to its original state (know as a factory reset).

Win8 has some kind of "refresh" option in its new boot manager.  It probably uses the contents of this partition for that to work.  If you remove this partition, that's probably NOT going to work.

Well, in addition to the C and D partitions, there's another two named "Recovery partition" one is 600 MB and the other is 20 GB. I believe one is the system utilities for backup and the 20 gigs is for creating windows restore points. There is also a 300MB EFI partition but I wouldn't touch those.

In this case D is really empty.

---

### Post by oldfred on 2012-11-14
Several users have reported that with 12.10 and grub2 2.00 and the 64 bit version of Ubuntu booted in UEFI mode, it does not matter if secure boot is on or not. 

I think grub2's os-prober's bug has not been fixed, so you will need Boot-Repair to add the correct Windows chain load entry. The os-prober creates a BIOS/MBR type chain entry which does not work. Boot-Repair can create it, or you can manually add the correct chain entry to 40_custom or create a 25_custom as Boot-Repair does.
Wrong style chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)

[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

Dual-boot Windows 8 and Ubuntu 12.10 on UEFI hardware
[http://www.linuxbsdos.com/2012/11/05/dual-boot-windows-8-and-ubuntu-12-10-on-uefi-hardware/](http://www.linuxbsdos.com/2012/11/05/dual-boot-windows-8-and-ubuntu-12-10-on-uefi-hardware/)

---

### Post by AstroLlama on 2012-11-15
Thanks for the replies :)
Partitioning went well, and install seemed successful, but now as oldfred correctly describes, the bootloader isn't functional. At boot, screen goes to a black Windows OS selection menu. choosing windows 8 works without problems, but Ubuntu studio does not. 

Strange that when you choose to load the Ubuntu option it gives a black screen saying "windows couldn't load properly." I will try to use boot repair as suggested here and in other posts as well.

I don't understand all the options, however. Boot repair gave an alert that EFI and /boot were detected, and to check the options. (this was expected)

below is the report made by boot repair, anymore suggestions?
[http://paste.ubuntu.com/1361496/](http://paste.ubuntu.com/1361496/)

PS thanks oldfred! you're being really helpful.

---

### Post by oldfred on 2012-11-15
It looks like you did not install in UEFI mode, it created a bios_grub partition which is required for BIOS boot. Normally with BIOS boot it writes grub into protective MBR which is just there in gpt partitioning to let old MBR tools know drive is formated. But you do not have grub installed.

You also have a separate /boot partition which should be ok, but usually not required with desktops. But with some systems we have seens BIOS that do not work if / (root) is too large or far into drive.

I do not see the Ubuntu efi entry. But Boot-Repair can convert a BIOS install to UEFI install. It uninstalls grub-pc and installs grub-efi and updates a couple of files. You then also have to use UEFI menu to boot ubuntu. And Boot-Repair has to fix Windows chain entry in grub menu.

---

### Post by AstroLlama on 2012-11-16
Alright now I'm confused again... I thought I needed to create a /boot (boot partition), / (root partition), and swap space.

there is already a windows EFI partition (sda1), but is that where I should have installed the boot loader, or should there be an Ubuntu EFI partition as well?

---

### Post by oldfred on 2012-11-16
With UEFI every system installs its boot loader files to the efi partition, it is like the MBR in BIOS, but allows multiple systems to all exist at once. Someone just filed a bug that multiple versions of Ubuntu cannot co-exist but you still use grub to boot anyway.

With BIOS we have always said to install grub2's boot loader to the MBR and not to a partition. With UEFI you do install the bootloader to the efi partition and there can only be one efi partition per drive.

The boot files in the efi partition are not the main boot files like the kernel, grub's menu & kernel files can be in a separate /boot partition or inside the / (root) partition.

Some have had issues with very large / (root) partitions or boot files that are way past the start of the drive. Not sure if BIOS or grub issue as it works for some and not others. May also be settings in UEFI/BIOS??
I normally suggest smaller / and separte /home if installing to a larger space. Still some have had issues and needed a separate /boot inside the first 100GB of a drive. But we have not seen a definitive reason why or bug report with anything other than a separte /boot. Or you may not know if you need it until you try to boot and it does not work. I have boot files near the end of my 650GB drive without issue, but it is a small / (25GB) partition.

---

### Post by AstroLlama on 2012-11-17
Ok, now it's starting to make more sense. 

I booted a usb pen in UEFI mode and now I'm going to repartition. If I understand correctly I should only have to make a / (root partition), the optional /home partition (good advice, oldfred), and swap space.

Now my only hesitation is the last step to choose the "Device for boot loader installation". I understand that It should be the in the preexisting EFI partition, but am nervous that this over right the existing entries needed for the windows install? Is this what boot repair will fix, should I not be worried?

I read that each OS's boot instructions are in their respective /EFI/[name] folders in the EFI partiton. what will happen?

---

### Post by oldfred on 2012-11-17
Yes, each system writes into sub-directories in the efi folder or partition. If you look at anyone with UEFI instal that has run Boot-Repair you will see the files.

I think most of these users posted BootInfo reports.

       UEFI dual boot two drives
[http://ubuntuforums.org/showthread.php?t=2072950](http://ubuntuforums.org/showthread.php?t=2072950)
[http://ubuntuforums.org/showthread.php?t=2031836](http://ubuntuforums.org/showthread.php?t=2031836)
UEFI boot Issue with Alienware X51 
[http://ubuntuforums.org/showthread.php?t=2039451](http://ubuntuforums.org/showthread.php?t=2039451)
UEFI dual boot trouble: Win7x64 - Ubuntu 12.04 LTS amd64
[http://ubuntuforums.org/showthread.php?t=2003442](http://ubuntuforums.org/showthread.php?t=2003442)
UEFI screen shots with choice to boot
[http://ubuntuforums.org/showthread.php?p=12030957#post12030957](http://ubuntuforums.org/showthread.php?p=12030957#post12030957)

---

### Post by AstroLlama on 2012-11-17
I read through all the posts on your links, though my problem is now very different! I made new partitions for / (root) and /home, and swap, then instructed the installer to load the boot loader on device sda1 (the efi partition).

Everything seemed to go well, I was able to boot into Ubuntu without problems but unable to boot into windows. I used boot repair, now neither OS will boot. At start up there's a terrible red fatal alert: Invalid signiture detected. check secure boot policy in setup

... nooooo

I'm on the system now using a live usb flash drive (at least that works...)
here's a new report [http://paste.ubuntu.com/1365296/](http://paste.ubuntu.com/1365296/)

two notes at the end of pastebin report:
Please do not forget to make your BIOS boot on sda1/efi/ubuntu/grubx64.efi file!

The boot files of [Ubuntu 12.10] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition...

Have I destroyed my computer?

---

### Post by AstroLlama on 2012-11-17
OK, after disabling secure boot in the bios both systems boot now. Not quite the solution i was expecting, and I still don't understand fully why the software signatures weren't working, but at least my computer wasn't turned into the proverbial brick.

A big thanks to oldfred for your patience and numerous informative links. If you ever come to Italia i will offer you a beer, or wine, or juice, at the bar whatever you want!

---

### Post by oldfred on 2012-11-17
Glad you got it resolved.

Did a cruise around the boot of Italy several years ago. Spent a couple of extra days in Rome and entire trip was wonderful. Really enjoyed Italy. Trip did not include Florence and that part which our daughter says is not to be missed so I may be back in a few years.

---

