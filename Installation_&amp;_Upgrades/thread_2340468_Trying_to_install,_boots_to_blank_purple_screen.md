---
title: "Trying to install, boots to blank purple screen"
date: 2016-10-19
forum: Installation &amp; Upgrades
---

### Post by ascharbarth on 2016-10-19
Just what the thread title says.  Trying to install 16.10 x64 on an empty partition alongside windows 10 and when the ubuntu stick I created boots into umei and I select install I get a bright purple screen with nothing else on it. 

 nomodeset does nothing. 
trying to open a terminal does not work. ([https://ubuntuforums.org/showthread.php?t=1743535](https://ubuntuforums.org/showthread.php?t=1743535))

System specs:
CPU:
INTEL i7-4790k
CPU Cooling:
Corsair H100i GTX (both)
GPU:
1x NVIDIA MSI GTX 970 4GB
GPU Cooling:
Stock (air)
RAM:
32GB HyperX Savage 8gb DDR3 2400 (x4)
Motherboard:
MSI Z97M
Primary Drive:
SSD Samsung 850 EVO 250GB SSD
Secondary Drive:
HDD WD Blue 1tb 7200 RPM
Optical Drive:
LG WD10EZEX 24x dvd+- RW
Sound Card:
Motherboard
Power Supply:
Cooler Master G750M
Case:
DIYPC Cuboid Green/Black Micro ATX
OS:
Windows 10
Display:
Samsung S24D390-4
Mouse:
Logitech G602
Mouse Pad:
Ratpadz XT
Keyboard:
Logitech K800
Headset:
SteelSeries 3Hv2
Speakers:
Logitech Z506
Webcam:
Canon EOS Rebel SL1 & Logitech C270
External microphone:
SteelSeries 3Hv2
VR Gear:
Not. Interested.
Gamepad:
Steam Controller
Joystick:
Saitek Pro X-56 Rhino

---

### Post by oldfred on 2016-10-19
Purple screen is BIOS, but your hardware is UEFI. Is Windows installed in BIOS boot mode? (probably UEFI)
And you want Ubuntu in same boot mode as Windows.
How you boot install media is then how it installs.

       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

And with UEFI, you have manually edit grub for installer and first boot after install or until you install nVidia driver from repository.

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Some systems need additional temporarily or permanent boot parameters.
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) 

On my Asus Z97, I had many UEFI settings to change. I turned off Secure Boot(Windows or "other"), turned on USB boot, then UEFI only boot from USB.
I had fast boot in UEFI, turned it off totally to install, but had setting for 3 sec delay which I then used, just so I have 3 sec to press key to get into UEFI if needed.
You may have similar settings:
 Asus-ar screenshots
[http://ubuntuforums.org/showthread.php?t=2258575&page=2](http://ubuntuforums.org/showthread.php?t=2258575&page=2) 


 Disable MSI Z87 fast boot to get it to work
[http://ubuntuforums.org/showthread.php?t=2272131&p=13258725#post13258725](http://ubuntuforums.org/showthread.php?t=2272131&p=13258725#post13258725)

---

