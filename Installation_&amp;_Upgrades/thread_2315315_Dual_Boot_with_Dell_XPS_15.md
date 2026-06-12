---
title: "Dual Boot with Dell XPS 15"
date: 2016-02-27
forum: Installation &amp; Upgrades
---

### Post by brian120 on 2016-02-27
I am new to Ubuntu and for learning purposes, am attempting to do a dual boot onto my Dell Windows 10 laptop and I am having a hell of a time getting Ubuntu to install.  


Details:
XPS 15 9550
Service Tag J88K72 
Windows 10 Pro




Attempt Dual boot setup number 1.
- Shrunk Windows to allow for 50G for my Ubuntu install
- Downloaded  Ubuntu 15.10 Desktop and created Bootable USB
- Went into Bios and turned UEFI secure boot to off.
- Booted from USB and and chose 'Install Ubuntu'
- I see the Ubuntu Logo and it doesn't progress at all beyond that point.


Attempt Dual boot setup number 2.
- Setup Bios to boot to legacy
- Reinstalled Windows 10 and shrunk volume.
- Booted from USB Mode and shose 'Unstall Ubuntu'
- I see the Ubuntu Logo and it doesn't progress at all beyond that point.


I tried the above with differen flavors of Ubuntu.  Xubuntu I actually progress a little farther but Xubuntu does not recognize my drives.  I researched and found that I needed to add a 'nvme' command in the boot up command line...but the install would just error out.


Any advise, troubleshooting suggestions would be appreciated.

---

### Post by oldfred on 2016-02-27
Very new hardware often needs some work arounds.
It takes Linux a bit to catch up with new hardware as vendors usually do not directly support Linux. And even those that provide some support may add features to kernel, but that has to go thru kernel release cycle, then kernel has to be added to distribution or another cycle.
You often have to add ppa, to get complied new versions of drivers and/or kernel and are then testing whether your new configuration all works.

I would only stay with UEFI boot. How you boot installer is then how it installs.
And I might try 16.04. You should not assume 16.04 as your main working system until released, but it has newer kernel & drivers. With 15.10, you probably have to add a ppa to install those same kernels & drivers and end up with half 15.10 and half 16.04 anyway.

If NMVe, you may want to download newest gparted and use it to partition drive.
 gparted should be at least version 0.24.0-1 to recognize NVMe devices
[http://gparted.sourceforge.net/index.php](http://gparted.sourceforge.net/index.php)
 Then use Something Else to choose partitions.


Some other Dell threads.
 Install Ubuntu 15.10 on Dell XPS 15 2015 9550 with Nvidia 960
[http://askubuntu.com/questions/736613/install-ubuntu-15-10-on-dell-xps-15-2015-9550-with-nvidia-960](http://askubuntu.com/questions/736613/install-ubuntu-15-10-on-dell-xps-15-2015-9550-with-nvidia-960)
Dell XPS 13 9343 Needs /EFI/Boot/Bootx64.efi to boot
[http://askubuntu.com/questions/731931/uefi-not-finding-a-bootable-system-on-xps13](http://askubuntu.com/questions/731931/uefi-not-finding-a-bootable-system-on-xps13)
[https://bugs.launchpad.net/dell-sputnik/+bug/1499323](https://bugs.launchpad.net/dell-sputnik/+bug/1499323)
Black Screen on Install (15.04 & 15.10) Dell XPS 8900 
[http://ubuntuforums.org/showthread.php?t=2303880](http://ubuntuforums.org/showthread.php?t=2303880)
Dell Xps 15 9550  Ubuntu 15.10 on new Infinity display (i7 6gen 16gbr UHD 4k touch)
[URL="http://ubuntuforums.org/showthread.php?t=2301071"]http://ubuntuforums.org/showthread.php?t=2301071


[/URL]

---

### Post by Javier_Macias-Guar on 2016-03-22
@brian120, I have a Dell XPS 15 9550 with working dual boot setup using windows 10 and ubuntu 16.04 (beta). You'll find the details at [http://ubuntuforums.org/showthread.php?t=2317843](http://ubuntuforums.org/showthread.php?t=2317843)

Hope it helps,

Javi

---

