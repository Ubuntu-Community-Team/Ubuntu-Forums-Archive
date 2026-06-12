---
title: "Dual Boot Cannot Load Windows 10 Through Grub"
date: 2016-09-06
forum: Installation &amp; Upgrades
---

### Post by zubbs1 on 2016-09-06
I had a dual boot Windows 10/Linux Mint.  Then I screwed up the linux system (not important to this discussion), and decided to load Ubuntu 16.04 over top of the linux mint partition.  

After the first reboot of ubuntu, I ran into some issues with the Ubuntu splash screen and my hardware setup that I finally was able to fix thanks to ([https://www.reddit.com/r/linuxquestions/comments/4x3sgt/after_working_fine_for_weeks_ubuntu_1604_now_gets/](https://www.reddit.com/r/linuxquestions/comments/4x3sgt/after_working_fine_for_weeks_ubuntu_1604_now_gets/))

According to gparted:
I have windows on sda. 
 I have ubuntu on sdb. 
 sda1 has a boot flag; sdb1 has a boot,esp flag.

I have verified that my ubuntu is in uefi mode:

```
dmesg | grep "EFI v"
```
[    0.000000] efi: EFI v2.00 by American Megatrends

Boot repair gives the following error:
> GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again.
Alternatively, you can retry after activating the [Separate /boot/efi partition:] option.

I tried selecting the separate boot/efi option, but still get the error message.
The GPT has me stumped, as ubuntu seems to be UEFI mode?  I'm at a loss.  Here is a link to the bootinfo report from boot-repair

[http://paste2.org/w8kA0O2j](http://paste2.org/w8kA0O2j)


Any help is appreciated.

Cheers.

---

### Post by ubfan1 on 2016-09-06
You have an UEFI machine, but appear to be running in legacy mode.  Windows is on an msdos partitioned disk, without an EFI partition, so it's probably installed in legacy mode.  You might as well install Ubuntu on sdb in legacy mode too, but sdb is a gpt partitioned disk, so it will need a grub-bios partition to hold the core.img part of the bootloader.  The way to tell which mode Ubuntu is running in is to look to see if /sys/firmware/efi exists.  Running in legacy mode, it will probably be absent.

---

### Post by dantheepicman on 2016-09-06
try reinstalling grub

---

### Post by mook765 on 2016-09-07
What happens if you directly boot to sda through your UEFI-BIOS?
If you can still boot to Windows that way I would convert sdb to MBR-partitioned disk, reinstall Ubuntu in legacy-mode, install Grub to sdb.
CheckBoot-order in UEFI-BIOS, sdb should be on first place, to boot to Grub-menu.
That keeps things simple.
To install Ubuntu in legacy-mode you have to boot the installer in legacy-mode.

---

