---
title: "Cool brand new laptop but disappointing Ubuntu 15.10 so far"
date: 2015-12-31
forum: Installation &amp; Upgrades
---

### Post by Sean_Tan on 2015-12-31
I just bought a Toshiba P50-C-18Q, which comes with 

* Dual Core, Intel i7-6500U
* 16GB RAM
* NVIDIA GeForce 950M (4GB)
* 1TB+8GB SSD hard drive
* Harmon Kardon speakers with DTS Sound

On the pre-installed Windows 7, everything seems smooth and snappy. But I am just experiencing crashes, and unexpected behaviours with Ubuntu 15.10. 

## Pre-Installation

I download and burn Ubuntu 15.10 onto a DVD.
First time on the boot menu, I selected "Check disc" and everything was fine.
Then, I go ahead "Install Ubuntu".

## Installation: Problem 1

Installation seemed to freeze (i.e. computer not doing anything for a very long time). It seemed to freeze at different points of the installation. Every time that happens, I have to restart the installation. I restarted about 5-6 times. I disabled Intel Smart Response Technology, that did help.

The installation did complete finally, but this instability gives me a bad feeling. How do I know the installation is okay? Are the drivers working well with the hardware?

## After installation: Problem 2

It hangs at the Ubuntu splash screen.

[ATTACH=CONFIG]266477[/ATTACH]

I restarted 5 times to no avail this time. Sometimes it went further

[ATTACH=CONFIG]266478[/ATTACH]

but still could not start. I got this error

`Dec 30 22:31:03 satellite kernel: [   24.083330] nouveau E[   PFIFO][0000:01:00.0] SCHED_ERROR [ UNK06 ]`

What does this mean?

## (Problem 3)

There is a workaround. I booted in recovery mode with this option `Ubuntu, with Linux 4.2.0-22-generic (recovery mode)`.
Then, I proceed to normal boot.

The option `Ubuntu, with Linux 4.2.0-22-generic (upstart)` seems to hang too.

## (Problem 4) Problem with graphics, using basic Graphics

This problem was solved by updating

    sudo apt-get update
    sudo apt-get dist-upgrade

## (Problem 5) File system checked failed

During safe mode, I selected `fsck`. But again, some sort of error.

[ATTACH=CONFIG]266479[/ATTACH]

## (Problem 6) Graphics again

When I maximise a terminal, I see this white screen

[ATTACH=CONFIG]266480[/ATTACH]

I am not sure how to attach syslog here, but here are some snippets

Dec 30 22:31:03 satellite systemd[1]: Started Remount Root and Kernel File Systems.
Dec 30 22:31:03 satellite kernel: [   24.019107] nouveau E[   PFIFO][0000:01:00.0] SCHED_ERROR [ UNK06 ]
Dec 30 22:31:03 satellite systemd[1]: Starting Ensure /etc/mtab is a symlink to /proc/mounts...
Dec 30 22:31:03 satellite kernel: [   24.020249] nouveau E[   PFIFO][0000:01:00.0] SCHED_ERROR [ UNK06 ]
Dec 30 22:31:03 satellite systemd[1]: Starting Flush Journal to Persistent Storage...
Dec 30 22:31:03 satellite kernel: [   24.027634] nouveau E[   PFIFO][0000:01:00.0] SCHED_ERROR [ UNK06 ]
Dec 30 22:31:03 satellite systemd[1]: Starting Load/Save Random Seed...
Dec 30 22:31:03 satellite kernel: [   24.028863] nouveau E[   PFIFO][0000:01:00.0] SCHED_ERROR [ UNK06 ]
Dec 30 22:31:03 satellite systemd[1]: Started Ensure /etc/mtab is a symlink to /proc/mounts.
Dec 30 22:31:03 satellite kernel: [   24.045693] nouveau E[   PFIFO][0000:01:00.0] SCHED_ERROR [ UNK06 ]
...

Dec 30 22:31:03 satellite systemd[1]: Starting LSB: AppArmor initialization...
Dec 30 22:31:03 satellite systemd[1]: Starting Clean up any mess left by 0dns-up...
Dec 30 22:31:03 satellite kernel: [   24.146899] nouveau E[   PFIFO][0000:01:00.0] SCHED_ERROR [ UNK06 ]



...

---

### Post by brian-mccumber on 2015-12-31
Have you tried to install the proprietary graphics drivers when you've successfully booted to the desktop? You can search for drivers in the dash and pick additional drivers and after a short wait you should see some graphics drivers options there. It's hard to read the errors from your images but the one with nouveau in it makes me think that Ubuntu's generic graphics drivers are not compatible with your graphics chip.

---

### Post by Sean_Tan on 2015-12-31
Thanks Brian.

It was showing this in "Additional drivers". Should I select option 1 or 2?

    NVIDIA Corporation: GM107M [GeForce GTX 950M]
    * This device is using an alternative driver.


    Option 1: Using NVIDIA binary driver - version 352.63 from nvidia-352 (proprietary, tested)
    Option 2: Using NVIDIA binary driver - version 352.63 from nvidia-352-updates (proprietary)
    Option 3: [selected] Using X.Org X server - Nouveau display driver from xserver-xorg-video-nouveau (open source)

Anyway, Option 1 did help with the problems.

It no longer hangs at the Ubuntu splash screen i.e. I can boot normally. When I maximise the terminal I no longer see the white screen.
The syslog also looks much better, with the re-assuring `Dec 31 16:45:15 satellite kernel: [    0.934592] [drm] Memory usable by graphics device = 4096M`
instead of a bunch of nouveau errors.

Life is better now, although it does not explain the hiccups (freezing) I experience during installation.

---

### Post by Sean_Tan on 2015-12-31
How do I make sure I am using the correct drivers for the CPU? In the additional drivers page, it is showing this

   Unknown
    * This device is using an alternative driver.


    [selected] Using Processor microcode firmware for Intel CPUs from intel-microcode (proprietary)
    Do not use the device

---

### Post by Sean_Tan on 2015-12-31
Also, regarding power management, the laptop specification says the battery should last 8 hours!

I haven't yet compare how the battery performs under Windows 7 and Ubuntu. Is it in general better to install tlp in Ubuntu?

[http://www.makeuseof.com/tag/easily-increase-battery-life-tlp-linux/](http://www.makeuseof.com/tag/easily-increase-battery-life-tlp-linux/)

---

### Post by buzzingrobot on 2015-12-31
In Additional Drivers, one of the drivers will be "Recommended".  Choose that one.

You may also select the microcode for the Intel CPU, if you wish.  I always do.

The proprietary drivers will be downloaded, processed and installed.  That may take at least several minutes or longer, depending on your internet connection.  

Once Additional Drivers says its done, you'll need to reboot to activate the drivers.

Nouveau is the open source driver for Nvidia cards. It's used by default if the Linux kernel detects an active Nvidia card. Open source developers don't have access to proprietary information from Nvidia, so they are on their own to create a driver for each new card that comes along. That means developers need to acquire -- purchase -- a machine with that card.  No company is paying a staff of Nouveau developers and buying every new laptop on the market.

New cards in new laptops are the most likely to have problems with Nouveau, then.

During the install, if you selected the option to download and install codecs and such during the install, that might have accounted for the delays you saw.The installer will also, I've noticed, often pause for some time before it displays the partitioning panel. 

fsck is the system file checker.  It will run automatically at a reboot if the machine was not shutdown properly.  Pushing the power button or ctrl-alt-del count as an improper shutdown.

---

### Post by oldfred on 2016-01-03
Both the Skylake processor & nVidia drivers make for issues. 
When you boot are you using nVidia or Intel Video. Can you set that in UEFI or is it automatic?

While not your model system, some of the issues are the same:
       Intel's Skylake Audio Firmware Lands
[http://www.phoronix.com/scan.php?page=news_item&px=Intel-Skylake-Audio-Firmware](http://www.phoronix.com/scan.php?page=news_item&px=Intel-Skylake-Audio-Firmware)
[http://www.phoronix.com/scan.php?page=news_item&px=Intel-SKL-BXT-Firmware-Blobs](http://www.phoronix.com/scan.php?page=news_item&px=Intel-SKL-BXT-Firmware-Blobs)
Skylake Intel Core i5 6500: A Great Skylake CPU For $200, Works Well On Linux, 4.3 kernel  for best graphics
[http://www.phoronix.com/scan.php?page=article&item=intel-i5-6500&num=1](http://www.phoronix.com/scan.php?page=article&item=intel-i5-6500&num=1)
Skylake needs this boot parameter:  i915.preliminary_hw_support=1
[http://www.phoronix.com/scan.php?page=news_item&px=Intel-SKL-Prelim-Support](http://www.phoronix.com/scan.php?page=news_item&px=Intel-SKL-Prelim-Support)
Xubuntu 14.04 - GRUB2 nomodeset brings wrong screen resolution - Acer TravelMate 4740 with Intel HD Graphics
[URL="http://ubuntuforums.org/showthread.php?t=2240620"]http://ubuntuforums.org/showthread.php?t=2240620
[http://www.phoronix.com/scan.php?page=news_item&px=WKS-GT2-No-Modeset](http://www.phoronix.com/scan.php?page=news_item&px=WKS-GT2-No-Modeset)
[/URL]
I think these are older models, so may not apply:

 Toshiba Satellite P50 model number: P50-A-01E Haswell processor
[http://ubuntuforums.org/showthread.php?t=2163854](http://ubuntuforums.org/showthread.php?t=2163854)
Turned NIC (Integrated Network Interface Controller) off and then booted off of USB. Was NOT an issue with any Linux distro just a quirk of the laptop.
 Am now running 13.10 daily and everything works. Also had to stick with EFI boot ON, Secure Boot disabled. Wouldn't boot off of any media or HDD when mode set to CSM.
Another users in same thread used Legacy mode and then NIC worked.
Toshiba P50 reset with pin hole on bottom
after tinkering, i found a little pinhole on the bottom of the laptop next to the RAM. used a paperclip to press it and now the BIOS is working again. 
[http://ubuntuforums.org/showthread.php?t=2237148](http://ubuntuforums.org/showthread.php?t=2237148)

---

