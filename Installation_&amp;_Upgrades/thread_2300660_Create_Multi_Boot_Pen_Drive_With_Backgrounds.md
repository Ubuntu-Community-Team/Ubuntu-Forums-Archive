---
title: "Create Multi Boot Pen Drive With Backgrounds"
date: 2015-10-27
forum: Installation &amp; Upgrades
---

### Post by coljohnhannibalsmith on 2015-10-27
Hello,

I recently purchased a 16GB Pen Drive From eBay, that had all kinds of diagnostic software and several Linux distributions that could be loaded from the menu. The menu also has a very slick HD background. I am currently using a dual-boot enterprise system, that I created by first installing Windows, then installing Ubuntu afterwards. The installer created the dual-boot menu automatically. I then loaded GRUB Customizer; and edited the menu text and added a background. I want to have the power to create a product like the one I purchased, with many more than two menu items. What apps do I need?

Thanks, Hannibal

---

### Post by yancek on 2015-10-27
I'm not sure I understand what you want.  A different background image on booting Grub?  Or just add more systems (Live CDs) to the usb drive?  You won't get many actual installs on a 16GB drive so I assume you want Live CDs?  You need to add the entries in the /etc/grub.d files such as 40_custom when using an installed system.  You probably need to clarify what you want to do.

---

### Post by ajgreeny on 2015-10-27
I am also lost about what you have and what you want to do with it.

I currently use a 16GB memory stick on which I installed grub, then added the .iso archive files of several distros to the stick and I can boot to a live OS of each distro from the grub menu that appears when I boot from it.  All the info that I used to do this is at [http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604), an old thread but still works, though I'm not sure how UEFI may effect things if you want to install one of the OSs from that memory stick.

Is that the sort of thing you are doing or trying to do, or is it that you simply want an image for the grub menu that you see?  If so I presume you will need to follow the instructions at [https://help.ubuntu.com/community/Grub2/Displays](https://help.ubuntu.com/community/Grub2/Displays) but I have never felt a need to have an image behind the grub menu so I am possibly the wrong person to give you advice about this.

---

### Post by oldfred on 2015-10-27
Some additional links:
 This will boot an ISO from a hard drive or any second drive or flash drive
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
[https://wiki.archlinux.org/index.php/Multiboot_USB_drive](https://wiki.archlinux.org/index.php/Multiboot_USB_drive)

---

### Post by coljohnhannibalsmith on 2015-10-28
> **ajgreeny said:**
> I am also lost about what you have and what you want to do with it.

I currently use a 16GB memory stick on which I installed grub, then added the .iso archive files of several distros to the stick and I can boot to a live OS of each distro from the grub menu that appears when I boot from it.  All the info that I used to do this is at [http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604), an old thread but still works, though I'm not sure how UEFI may effect things if you want to install one of the OSs from that memory stick.

Is that the sort of thing you are doing or trying to do, or is it that you simply want an image for the grub menu that you see?  If so I presume you will need to follow the instructions at [https://help.ubuntu.com/community/Grub2/Displays](https://help.ubuntu.com/community/Grub2/Displays) but I have never felt a need to have an image behind the grub menu so I am possibly the wrong person to give you advice about this.

I think what you've suggested is the closest to what I'm trying to do. Since it appears I wasn't that clear; I realized that I needed to really examine this drive. Well, he's using a single FAT32 partition on the memory stick; and the menu looks like the following:

-----------------------------------------------------------------------------------------------------
                                                     MultiBoot
-----------------------------------------------------------------------------------------------------
Boot from First Hard Drive (default)

   Hiren's Boot CD 15.2

Antivirus                 ->

Recovery Tools         ->

Linux Distributions    ->

-----------------------------------------------------------------------------------------------------
                                          Press [Tab] to edit options

This is a fairly sophisticated menu and uses 2 level nesting. Upon examining the contents of the stick, it appears he is doing this with GRUB. I had no idea nesting was possible with GRUB.

It just occurred to me that his config file must be in there somewhere. Perhaps, I can borrow and modify some of his code. I'm still a bit foggy on how to install GRUB to a memory stick, independent of a distro's installer; but I assume the literature you referenced covers some of that.

I have attached several images to show the contents of the stick. In the mean time I've got some reading to do.

---

### Post by oldfred on 2015-10-28
I prefer to use grub2, as then my standard grub2 can also be used to boot ISO or other installs. But if you use a different boot loader you have to also learn how it works. I started using grub2 loop mount before most of the scripts became available, but doing it yourself then you understand process a bit better. Many installs can be booted directly from ISO which makes it easy just to copy ISO to flash drive and correctly configure a grub entry. But a full installs do not boot directly and you have to extract /boot so boot that and have boot configured to mount rest of install. 

The flash drive you purchased may have just been one of these. 
 These are scripts to install many ISOs. Some that will not loopmount by installing a kernel and boot image.
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk w/grub2
[https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriveFlashDriveUSBDisk](https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriveFlashDriveUSBDisk)
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
[http://sourceforge.net/projects/multibootusb/files/](http://sourceforge.net/projects/multibootusb/files/)
[https://sourceforge.net/projects/multibootusb/files/](https://sourceforge.net/projects/multibootusb/files/)
MultiSystem Another LiveUSB Multiboot French(translate) w/grub2 
[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)
[http://ubuntuforums.org/showthread.php?t=2175738](http://ubuntuforums.org/showthread.php?t=2175738)
Uses grub4dos to boot many ISO and other bootable files
[http://www.rmprepusb.com/tutorials/72---easyboot---a-grubdos-multiboot-drive-that-is-easy-to-maintain/e2bv1](http://www.rmprepusb.com/tutorials/72---easyboot---a-grubdos-multiboot-drive-that-is-easy-to-maintain/e2bv1)

How you install grub to flash drive varies depending on whether you want the older BIOS boot or the newer UEFI boot. I have flash drives configured for either by using gpt partitioning and having both FAT32 efi partition and bios_grub for grub BIOS boot. You can also use syslinux like the Ubuntu installer for BIOS boot with just the one FAT32 partition.

       Flash drive to boot in UEFI or BIOS - sudodus
[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)
[https://help.ubuntu.com/community/Installation/FromUSBStick#Ubuntu_single_boot_in_UEFI_mode](https://help.ubuntu.com/community/Installation/FromUSBStick#Ubuntu_single_boot_in_UEFI_mode)
A new and so far successful attempt to create a stable portable system, that works in UEFI and BIOS mode
[http://ubuntuforums.org/showthread.php?t=2213631&p=13262506#post13262506](http://ubuntuforums.org/showthread.php?t=2213631&p=13262506#post13262506)
[http://spblinux.de/blog/2013/06/uefi-and-bios-bootable-usb-stick-with-grub2/](http://spblinux.de/blog/2013/06/uefi-and-bios-bootable-usb-stick-with-grub2/)

---

### Post by yancek on 2015-10-28
> It just occurred to me that his config file must be in there somewhere. 

Take a look at the syslinux.cfg file.  There should also be an isolinux.cfg file under HBCD to check as well as grub.cfg under /boot/grub and compare them to the menu you see on boot.

You can install Grub to a flash drive under the /boot directory the same way you install Grub on an installed system.  Big difference is that when doing this, you will not have a grub.cfg file and you will need to create a proper one using a template from another system.   If this system is booting with Grub 2, it should be a simple matter of putting a correct loopback menuentry in the grub.cfg file, assuming the iso is capable of being booted in that manner.  Otherwise, you would need to extract the iso to the flash drive which gets cumbersome.  

The flash drive I have with HBCD has it and it's various utilities on one partition, Ubuntu iso files on another with Grub in the MBR chainloading syslinux on another partition.  Keeping the iso files on a separate partition  is another option.

---

### Post by coljohnhannibalsmith on 2015-11-06
> **yancek said:**
> Take a look at the syslinux.cfg file.  There should also be an isolinux.cfg file under HBCD to check as well as grub.cfg under /boot/grub and compare them to the menu you see on boot.

You can install Grub to a flash drive under the /boot directory the same way you install Grub on an installed system.  Big difference is that when doing this, you will not have a grub.cfg file and you will need to create a proper one using a template from another system.   If this system is booting with Grub 2, it should be a simple matter of putting a correct loopback menuentry in the grub.cfg file, assuming the iso is capable of being booted in that manner.  Otherwise, you would need to extract the iso to the flash drive which gets cumbersome.  

The flash drive I have with HBCD has it and it's various utilities on one partition, Ubuntu iso files on another with Grub in the MBR chainloading syslinux on another partition.  Keeping the iso files on a separate partition  is another option.

Well, I finally figured out how he got the menus to nest. In syslinux.cfg he's written a couple of lines to call the linux distros in the linux.cfg file, like this:

```
# start linux
label -
menu label Linux Distributions ->
config linux.cfg
# end linux

```

Then:

```
#start tails 
label - 
menu label ^Tails 1.5.1 (Privacy and Anonymity) 
menu indent 1 
config /multiboot/tails-i386-1.5.1/isolinux/isolinux.cfg 
append /multiboot/tails-i386-1.5.1/isolinux 
text help 
Security-focused Debian-based Linux distribution aimed at preserving 
privacy and anonymity. All its outgoing connections are forced to go 
through Tor, and direct (non-anonymous) connections are blocked. 
The system will leave no trace on the machine unless explicitly told 
to do so. 
endtext 
#end tails

```

This was a lot more straight forward than I had imagined.

So now, I'm getting various kinds of errors with some distros after installing them with "MultiBootUSB." The first distro I tried to install was Clonezilla-live-2.4.2. Here's the code to load it:

```
#start clonezilla-live-2.4.2-10-amd64
LABEL clonezilla-live-2.4.2-10-amd64
MENU LABEL clonezilla-live-2.4.2-10-amd64
BOOT /multibootusb/clonezilla-live-2.4.2-10-amd64/syslinux/debian.bs
#end clonezilla-live-2.4.2-10-amd64
```

Here are the errors I got:

```
Undef symbol FAIL: __syslinux-debug-enabled
Failed to load libcom32.c32
Failed to load COM32file vesamenu.c32

```

These messages just looped forever.

Does anyone recognize these errors and understand what should be happening that isn't:confused:?

Thanks, Hannibal

---

### Post by yancek on 2015-11-06
The BOOT line in your syslinux.cfg file for clonezilla looks a little odd.  Are you actually trying to directly boot the iso file?  I had clonezilla on a multii-boot flash but booted it with Grub2 and had to extract the iso before it would work.  This was several years ago.  Also, you should have a COM32 directory with a vesamenu.c32 file in it somewhere.  I don't really use syslinux or isolinux so can't suggest much else.

---

### Post by coljohnhannibalsmith on 2015-11-06
> **yancek said:**
> The BOOT line in your syslinux.cfg file for clonezilla looks a little odd.  Are you actually trying to directly boot the iso file?  I had clonezilla on a multii-boot flash but booted it with Grub2 and had to extract the iso before it would work.  This was several years ago.  Also, you should have a COM32 directory with a vesamenu.c32 file in it somewhere.  I don't really use syslinux or isolinux so can't suggest much else.

MultiBootUSB created the BOOT line. I suspect it should be pointed at something else; but I don't know what. There's a file called Clonezilla-Live-Version, that has the following contents:

```
clonezilla-live-2.4.2-10-amd64
This Clonezilla live iso file was created by this command:
ocs-iso -s --extra-boot-param quiet -y 6.03 -i 2.4.2-10-amd64

```

This leads me to believe that you're probably right about the iso file needing to be extracted.

Also, in the linux directory of a Clonezilla pen drive that was installed with UNetBootin, there's a script called "makeboot.sh."

---

### Post by coljohnhannibalsmith on 2015-11-08
I also ran into problems when I installed Knoppix. When I ran it in QEMU I got the following error:

Linux Kernel 3.16.3-64, 995 MB RAM
CPU0: QEMU Virtual CPU version 2.0.0 @ 2095MHz, 512KB Cache.
Could not mount disk to /mnt.system.
Starting debuggung Shell...
sh: Can't access tty; job control turned off.
/ # _

Please see attachment.

Apparently, Knoppix is aware that it's not on a DVD!

Both TAILS and Knoppix have USB installers; but using this option formats the entire Pen-Drive; which is what MultiBootUSB was designed to get around. The creator of the original Pen Drive somehow managed to get TAILS installed. What happened when I loaded TAILS for the first time, is that it immediately complained of being out-of-date; and then complained that it could not be updated because it was not installed using the native installer.  Apparently Linux distros have a varying degree of gregariousness, that must be taken into consideration when using this tool.

I've been thinking about Installing TAILS or Knoppix first using the native installers; then using MultiBootISB to install the rest. However, this method will only work for one anti-social distro. If I want to install more than one (let's say three) Clonezilla, Knoppix and TAILS to the same pendrive, I've got real problems. The only other solution I can think of is to partition the pendrive; but then I run into the problems of mounting and unmounting the appropriate partitions; and calling them from a script located on one of the partitions. Wow, this just keeps getting worse.

Any help appreciated.

Thanks, Hannibal

---

### Post by sudodus on 2015-11-08
Knoppix and Tails are included in the following tutorial from Arch.

[https://wiki.archlinux.org/index.php/Multiboot_USB_drive](https://wiki.archlinux.org/index.php/Multiboot_USB_drive)

I don't know if things have changed in the boot configuration, but at least you can try according to the suggested menuentries.

But ***Tails*** might not be quite safe when booted via 'grub and iso', so Tails should be used from its own pendrive.

> Warning: Emergency memory erasure does not seem to work when booting this way.

---

