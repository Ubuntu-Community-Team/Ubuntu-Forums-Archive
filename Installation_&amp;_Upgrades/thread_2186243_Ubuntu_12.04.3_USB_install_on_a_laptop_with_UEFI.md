---
title: "Ubuntu 12.04.3 USB install on a laptop with UEFI"
date: 2013-11-06
forum: Installation &amp; Upgrades
---

### Post by W-Unit on 2013-11-06
--EDIT--
Using the 64-bit version resolved the issue; thanks :)

Hi :)

I'd like to install Ubuntu alongside Windows 8 in my new Toshiba Satellite laptop, which has EFI (instead of BIOS).

I've spent almost the entire last 24 hours trying to create a USB drive that the Toshiba will boot from, to no avail.
I have, however, learned how to reliably access the EFI settings and select a boot device - neither of which, it turns out, are performed by pressing any keys during boot-up. Little victories.

Anyways, I've got a different desktop that's running Saucy, so my goal is to use that machine to create the USB drive that will install Ubuntu on the laptop.
When I tried to do this as normal using Kubuntu's Startup Disk Creator (with the image file named ubuntu-12.03.3-desktop-i386), I was able to boot the USB drive as expected on the desktop machine. However, on the laptop machine, when I attempted to manually select the USB as the boot device, UEFI told me: "System doesn't have any USB boot option. Select another device." or something.

Before you refer me to Google, I've already found a good deal of info on this topic. The problem is, I don't really understand the info that I've found. What I have learned of the issue is the following:
> 1) In order to be recognized by EFI as "bootable," the file system must be fat32
2) There is some connection to .efi files and a directory called /boot/efi
3) elilo is a command-line tool to "install EFI boot loader."

My problems:
1) "Startup Disk Creator" seems to create vfat filesystems. I assume this is a problem since fat32 is necessary according to UEFI spec. Is there any way to change this so Startup Disk Creator uses the correct file system?
2) I've got elilo installed, but I'm not sure how to proceed with using it to achieve this goal?


If you think I could achieve my goals more easily by using Windows 8 for this whole operation, instead of using my other Ubuntu machine to create the USB drive, please let me know. But making and formatting drives and file systems is something I would expect Linux to be better suited for :)
I have, however, already tried WinUSB Maker; this program complained that the iso file (same one I had used successfully with Startup Disk Creator to boot my desktop) was invalid, something about NT.6 or NTX6 or something.


Here are some info sources I read, but couldn't really fully understand...
[https://wiki.archlinux.org/index.php/UEFI_Bootloaders](https://wiki.archlinux.org/index.php/UEFI_Bootloaders)
[http://superuser.com/questions/415198/make-uefi-gpt-bootloader-ssd-usb-linux-and-windows-work-together](http://superuser.com/questions/415198/make-uefi-gpt-bootloader-ssd-usb-linux-and-windows-work-together)
[https://www.linuxquestions.org/questions/slackware-14/uefi-boot-support-in-the-slackware-installer-4175453960/](https://www.linuxquestions.org/questions/slackware-14/uefi-boot-support-in-the-slackware-installer-4175453960/)
[http://superuser.com/questions/415198/make-uefi-gpt-bootloader-ssd-usb-linux-and-windows-work-together](http://superuser.com/questions/415198/make-uefi-gpt-bootloader-ssd-usb-linux-and-windows-work-together)
[http://unix.stackexchange.com/questions/41738/booting-linux-from-usb-using-efi](http://unix.stackexchange.com/questions/41738/booting-linux-from-usb-using-efi)

Thanks for your time guys, and have a great day!

---

### Post by oldfred on 2013-11-06
The vfat driver is for fat32 (and other FAT versions).

You have to have a 64 bit version for UEFI install or the amd64 version of Ubuntu or other flavors.

       Also instructions for DVD or USB flash drive
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to flash or DVD.
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

You need to follow these instructions with Ubuntu. 

 Shows install with screen shots.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot. required for UEFI & grub bug fixes
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Also lots more info in links in my signature.

Other Toshiba installs

 Toshiba Satellite P50 model number: P50-A-01E Haswell processor
[http://ubuntuforums.org/showthread.php?t=2163854](http://ubuntuforums.org/showthread.php?t=2163854)
Turned NIC (Integrated Network Interface Controller) off and then booted off of USB. Was NOT an issue with any Linux distro just a quirk of the laptop.
 Am now running 13.10 daily and everything works. Also had to stick with EFI boot ON, Secure Boot disabled. Wouldn't boot off of any media or HDD when mode set to CSM.
Toshiba Satellite P75 intel hd 4600 needed acpi_osi=Linux acpi_backlight=vendor
[http://ubuntuforums.org/showthread.php?t=2161204](http://ubuntuforums.org/showthread.php?t=2161204)
Toshiba laptop C850 Windows 7 with upgrade to 8 version -  sudodus
[http://ubuntuforums.org/showthread.php?t=1769482&p=12606025#post12606025](http://ubuntuforums.org/showthread.php?t=1769482&p=12606025#post12606025)
 [SOLVED] Can't install Windows 8 & Ubuntu in Toshiba Portege Z930 with explanation how by OP feb 2013
[http://ubuntuforums.org/showthread.php?t=2114290](http://ubuntuforums.org/showthread.php?t=2114290)

---

### Post by W-Unit on 2013-11-06
Actually, I just got the USB drive to boot! Got to step out soon so I'll make this quick and can give you more details later if you need them

I am 99% sure I have been using a 64-bit image this entire time: ubuntu-12.04.3-desktop-i386.iso I downloaded it from the Ubuntu website download page very recently.

Anyways, I got it to boot to something other than Windows! Hooray!

But, all I get is a black-and-white terminal screen titled "GNU GRUB version 1.99-21ubuntu3.10"
I get a grub> prompt where I can type.

The way I got the USB drive to work was weird and not by following any instructions... so not sure if it's really a good way, but at least it got it booting! I can tell you more about how I did this if needed.

I've let the laptop sit at that screen for some time and nothing happens.

Thanks! :)

---

### Post by oldfred on 2013-11-06
You will be able to boot the 32 bit version in BIOS/CSM/Legacy mode. But you really want the 64 bit version.

This is the 64 bit version.
ubuntu-12.04.3-desktop-amd64.iso

---

