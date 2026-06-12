---
title: "HOWTO: install Kubuntu (Ubuntu) 13.04 on an Acer Aspire V5-122P (0889)"
date: 2014-01-31
forum: Installation &amp; Upgrades
---

### Post by Cinderboot on 2014-01-31
This HOWTO may also apply to the V5-122P-0408 and other variants.

AMD A4 1250 @ 1GHZ (64 bit)
4GB RAM

lspci gives:

00:00.0 Host bridge: Advanced Micro Devices [AMD] Family 16h Processor Root Complex
00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Kabini [Radeon HD 8210]
00:01.1 Audio device: Advanced Micro Devices [AMD] nee ATI Device 9840
00:02.0 Host bridge: Advanced Micro Devices [AMD] Family 16h Processor Function 0
00:02.3 PCI bridge: Advanced Micro Devices [AMD] Family 16h Processor Functions 5:1
00:10.0 USB controller: Advanced Micro Devices [AMD] FCH USB XHCI Controller (rev 01)
00:11.0 SATA controller: Advanced Micro Devices [AMD] FCH SATA Controller [IDE mode] (rev 40)
00:12.0 USB controller: Advanced Micro Devices [AMD] FCH USB OHCI Controller (rev 39)
00:12.2 USB controller: Advanced Micro Devices [AMD] FCH USB EHCI Controller (rev 39)
00:13.0 USB controller: Advanced Micro Devices [AMD] FCH USB OHCI Controller (rev 39)
00:13.2 USB controller: Advanced Micro Devices [AMD] FCH USB EHCI Controller (rev 39)
00:14.0 SMBus: Advanced Micro Devices [AMD] FCH SMBus Controller (rev 3a)
00:14.2 Audio device: Advanced Micro Devices [AMD] FCH Azalia Controller (rev 02)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] FCH LPC Bridge (rev 11)
00:14.7 SD Host controller: Advanced Micro Devices [AMD] FCH SD Flash Controller (rev 01)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 16h Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 16h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 16h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 16h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 16h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 16h Processor Function 5
01:00.0 Network controller: Atheros Communications Inc. AR9565 Wireless Network Adapter (rev 01)



If you are like me, you don't care what OS is on the machine, you are probably going to wipe it clean anyways and install your favorite flavor of Linux. I've been clean from MS Windows for 2 years now and I never plan on using it again.


Getting everything to work on this sleekbook was an odyssey, so I will break it down fairly simple.


This Acer comes with UEFI and a "Legacy" option for traditional BIOS.


The UEFI is InsydeH20 and version 2.04 I believe.


I had a hard time disabling "Secure Boot" because it's greyed out and you can't change the settings. Fix: Set an Admin password and it allows you to change those options.


I wanted to install Kubuntu 12.04 LTS on this Acer, but it was not easy.
Instead, I went with 13.04 and I will document the steps here so you can be up and running quickly. I'll explain the whole story later. Ubuntu and Kubuntu are very much alike, so I'm guessing Ubuntu would install in the same manner.


START:


1.- Put Ubuntu (Kubuntu 13.04 64 bit) on a flash drive. If you forget how to do this (I always forget since I rarely make bootable flash drives) do:


$ dd bs=4M if=kubuntu.13.04-x64.iso of=/dev/sdb


(where kubuntu.13.04-x64.iso is the 64 bit CD image you downloaded and /dev/sdb is your flash drive)


2.- Go into Windows and resize your hard disk so you have enough space for linux (mine is 100GB, 95GB for / and 5GB swap)


3.- Reboot (it seems "Fastboot" is ignored when you reboot in Win8)


4.- Press F2 at the "Acer" logo as soon as it boots to get into the UEFI.


5.- Change the BIOS mode to "Legacy". (I couldn't get the video drivers to work in UEFI mode)


6.- Plug in the flash drive


7.- Save and exit the BIOS


8.- Press F2 again to get into the BIOS and make "USB HDD" first in the boot sequence and make "HDD" second. I put Win8 last, after "Network boot" (FU Bill). You should notice the USB HDD says "Kubuntu 13.04"


9.- Save and exit BIOS.


10.- Install on the free space (100GB) you created.


:END


Whole time from installation to up & running was about 20 min.

The integrated Bluetooth is RECOGNIZED but doesn't work. I later found that the drivers are still under development. So I went to Best Buy and got a Rocketfish RF-MRBTAD micro adapter.
A quick search tells you to:
$ sudo hciconfig hci1 reset
and
$ sudo restart bluetooth


Then the KDE BT manager will be able to scan for devices.

---

