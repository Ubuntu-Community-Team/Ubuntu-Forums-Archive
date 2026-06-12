---
title: "Installing 12.04.3 on a Acer Aspire V5-131-2629"
date: 2013-11-15
forum: Installation &amp; Upgrades
---

### Post by SmallWorld on 2013-11-15
[B]The short of it:
[/B]The default 12.04.3 64bit DE install works good with a few tweaks.  I haven't tested Bluetooth or external monitors yet.

[B]The long of it:
[/B]Following is the process I used.

This laptop comes with Windows 7 Home Premium, even though we're well into the Windows 8 era.  Bless your hearts, Asus.
The 500GB hard drive comes with three partitions:
- sda1 (ntfs) 19.3GB - the Windows7 recovery partition.
    - sda2 (ntfs) 104.9MB - the Windows7 loader
- sda3 (ntfs) 480.7GB - the Windows7 "C:" drive
 I left the hard drive in this configuration (no editing of the parition table) prior to installing Ubuntu.

The firmware (BIOS) is UEFI, specifically InsydeH20.  This means the install-from-Windows (Wubi) installer won't work.  Also, this UEFI does not support booting from a SD card.  You must boot and install from a USB device.

[LIST]
[*]I put the 64bit Desktop Edition 12.04.3 installer onto a USB drive and set the laptop's UEFI to boot from the USB. 
[*]Upon booting from the USB I chose the option to Install Ubuntu directly. 
[*]I chose to install Updates and 3rd Party Software during the OS install. 
[*]I was able to connect to wifi from within the installer program without any issues, although the wifi connection interface was a little laggy. 
[*]I chose to "Install Ubuntu alongside Windows 7". 
[*]The next step was to use the poorly-labeled drive space divider.  This allows you to shrink the sda3 partition (on the left side of the visual divider), making room for Ubuntu (on the right side of the visual divider).  I made the left side of the divider 100GB. 
[*]I let the installer do its thing.  I chose to encrypt my home folder. 
[*]When finished, I restarted. 
[/LIST]
GRUB and then Ubuntu booted up without any hitches.
The Additional Drivers control indicated that "No proprietary drivers are in use on this system."  Sweet.



GRUB needs to be modified to get the keypad brightness buttons to work:
```
sudo gedit /etc/default/grub
```Change the line
*GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"*
to *GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi="*
Then:```
sudo update-grub
```Then restart.



After a while, the wifi just stopped working, and apparently this is common.  A number of forum pages reveal the permanent fix:```
sudo gedit /etc/modprobe.d/ath9k.conf
```Type in the following:```
options ath9k nohwcrypt=1
```Save and close this file, then:```
sudo modprobe -rfv ath9k
sudo modprobe ath9k
```



The touchpad is a buttonless model, so it's a PITA to right-click on anything.  I'm considering installing Synaptiks to be able to use a two-fingered tap as a right-click but just can't swallow that Synaptiks needs 300MB to install.

The system now runs like a champ.  Wifi works, full-screen Youtube videos play smoothly, speakers work, headphones work, and Windows7 still boots up and runs as good as it ever did.  I haven't tested Bluetooth or external monitors yet.  I use Gnome with No Effects, so can't speak for the performance of the Unity or Compiz.

---

### Post by wn1ytw on 2014-02-02
> **SmallWorld said:**
> 
The firmware (BIOS) is UEFI, specifically InsydeH20.  This means the install-from-Windows (Wubi) installer won't work.  Also, this UEFI does not support booting from a SD card.  You must boot and install from a USB device.

[LIST]
[*]I put the 64bit Desktop Edition 12.04.3 installer onto a USB drive and set the laptop's UEFI to boot from the USB
[/LIST]


I wonder exactly which file, and from where, you put on the USB and did you use something like uunetbootin?
(sorry to be such a noob, I've just gotten confused and wary after so much reading on how to install!) I will be trying this on that laptop in a few days :)

I will use this if I see nothing better: [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu)

scott

---

### Post by SmallWorld on 2014-02-05
If you're still after an answer, I did indeed just follow the instructions on the Ubuntu.com site to create a bootable USB stick.&nbsp; I used the Acer to create the USB stick, by booting into Windows when I first received the Acer and I followed the instructions at [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows) .

---

### Post by wn1ytw on 2014-02-06
I did the USB drive thing when I posted -quick and easy, thanks. feeling comfy with booting and changing the UEFI boot order took me some time, mostly in getting the courage to plug the stick into the new laptop! Unsaid, and I did not find a step by step of changing the boot order, it was not hard - 

just plug the drive in -  
F2 at boot to enter UEFI, and 
made a change to the order of devices and a choice appeared that was  not there for my USB Kensington stick! 
I moved that up and exit saved.
When I booted it booted to Ubuntu. 

Waiting for some new disks to get here before making a set of the factory recovery to install. It worked nicely 'Live' though, thanks - I was nervous with the UEFI.

---

### Post by wn1ytw on 2014-02-24
never mind

---

### Post by wn1ytw on 2014-02-24
The only hiccup I had was that the windows partition needed to be shrunk before booting to the USB stick else only 2 options appeared: the install over windows and something else. To get the alongside option I needed to have free space available, and as I shrunk sda 3 by 100Gb, that negated the sizing tool in Ubuntu's install. 

Thanks for showing me the way! I now have a dual boot Windows 7/Ubuntu 12.04 LTS LAPTOP.

---

### Post by mthos on 2014-04-26
Hi, 

I recently installed Ubuntu on my v5-131. I didn't encounter any problems with either 13.10 nor 14.04. However: I can't get the sd card reader to work.

Anyone got a solution for me?

---

### Post by mthos on 2014-04-27
Here's some more info:

The sd-card reader in question is: Broadcom Corporation BCM57765/57785  

I allready found this diskussion: [http://ubuntuforums.org/showthread.php?t=2178199](http://ubuntuforums.org/showthread.php?t=2178199)
which states, that this patch would help: [https://chromium.googlesource.com/chromiumos/third_party/kernel-next/+/fd1acc54a6b3db4e6503ccc4a9349f28b436031a](https://chromium.googlesource.com/chromiumos/third_party/kernel-next/+/fd1acc54a6b3db4e6503ccc4a9349f28b436031a)

... so can anyone point me to the direction of a guide on how to apply this patch?

ps. also by "didn't encounter any problems" I mean wifi doesn't work properly since 14.04 (no problems with 13.10)

---

