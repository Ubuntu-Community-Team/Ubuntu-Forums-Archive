---
title: "Ubuntu fails to recognize Windows 8 OS on installation"
date: 2014-02-01
forum: Installation &amp; Upgrades
---

### Post by henadinn on 2014-02-01
Hello, I am attempting to load Ubuntu 12.10 on a newer Toshiba model  computer which uses the UEFI boot mode. I switched boot mode to CSM  settings and disabled the security boot. Then I went onto install ubuntu but there's no option for a simple dual boot. The menu reads "The computer currently has no detected operating systems, what would you like to do?" Then prompts to either Erase disk, which I do not want to do and the 'something else' option. I'm unfamiliar with partitions and I just want it to be simple for my mother to choose which OS she'd like to use at each startup. I'm fairly new to the OS and the installation has been very difficult for me on this pc, but very easy on my own older laptop which I installed ubuntu on with wubi. If I need to be more specific please let me know. Thanks for any help.

---

### Post by oldfred on 2014-02-01
Probably better to use 13.10 64 bit version.

And leave CSM mode on but boot in UEFI mode. Very new systems need that for an issue with Intel i915 driver.

Only boot in CSM mode if you have a system that will not eve boot Ubuntu in UEFI mode.

 Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot. required for UEFI & grub bug fixes
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

        Toshiba Satellite P50 model number: P50-A-01E Haswell processor
[http://ubuntuforums.org/showthread.php?t=2163854](http://ubuntuforums.org/showthread.php?t=2163854)
Turned NIC (Integrated Network Interface Controller) off and then booted off of USB. Was NOT an issue with any Linux distro just a quirk of the laptop.
 Am now running 13.10 daily and everything works. Also had to stick with EFI boot ON, Secure Boot disabled. Wouldn't boot off of any media or HDD when mode set to CSM.
Another users in same thread used Legacy mode and then NIC worked.
Toshiba Satellite P75 intel hd 4600 needed acpi_osi=Linux acpi_backlight=vendor                               
[http://ubuntuforums.org/showthread.php?t=2161204](http://ubuntuforums.org/showthread.php?t=2161204)
How to install Ubuntu 13 dual boot with Windows 8 Ubuntu Studio
[http://ubuntuforums.org/showthread.php?t=2186838](http://ubuntuforums.org/showthread.php?t=2186838)

---

### Post by PotatoHead007 on 2014-02-01
Just remember to first create a partition by shrinking the HDD from inside Windows 8, otherwise it will corrupt your files over time. :)
When you get to installing, choose "Do something else", then select the xxGB of free space you made. Works with me, but to be safe, back-up your Windows.

---

