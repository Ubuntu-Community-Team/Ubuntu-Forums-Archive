---
title: "Installer crashes - Ubuntu 16.04 on Dell XPS 15 9550"
date: 2016-10-13
forum: Installation &amp; Upgrades
---

### Post by sergeip2 on 2016-10-13
I am trying to install Ubuntu 16.04 on my Dell XPS 15 9550 laptop (16GB RAM, 512GB SSD, NVIDIA GeForce GTX 960M) [[retailer link]("http://www.johnlewis.com/dell-xps-15-notebook-intel-core-i7-16gb-ram-512gb-ssd-full-hd-15-6-silver/p3033738")]. I have created a USB install disk from the official iso, and have booted into the graphical installer from the USB disk. The first couple of dialogs work fine (asking for Wifi credentials, updates/third-party packages). When I get to the installation partitions dialog, the installer crashes:
[LIST=1]
[*]An error popup appears (Ubuntu has experienced an internal error...)
[*]The partition list in the dialog is empty
[*]When I press any button in the dialog, the desktop disappears, dropping down to a terminal with kernel error messages. I cannot get the desktop or even a TTY using Ctrl+Alt+Function keys. Two types of error messages continuously appear on the terminal:
[/LIST]

[LIST=|INDENT=2]
[*]Error: Driver 'ebridge' is already registered, aborting...
[*]nvidia-nvlink: alloc_chrdev_region failed: -16
[/LIST]


Can anyone suggest what to do? I guess the problem is with nVidia drivers, which I could update/disable once the installation is complete. But is there a way to get through the installation if the desktop keeps crashing?

---

### Post by Bucky Ball on 2016-10-13
*Thread moved to **Installation and Upgrades**.*

Better support for this here. ;)

Welcome. Probably yes. Do not click 'Install proprietary drivers' or 'Update during install'. You can do both later. There is a driver ready and waiting for your GPU once installed to hard drive. 

Don't worry about wireless or internet. Install offline. That can be fixed later also. If it's working now it may work 'automagically' on first boot.

If you still don't get anywhere ... when you boot from the install USB and get to the purple screen with the line along the bottom (I think), hit any key then F6 should get you a pop-up option list. Choose 'nomodeset' and proceed. Can you get further?

Are you dual-booting with Windows? If so, you will probably need to be installing Ubuntu in EFI. Whatever mode Windows is installed in you should be installing Ubuntu in.

You are using the AMD64bit version?

---

### Post by sergeip2 on 2016-10-13
Yes, I am using the AMD64 version, dual-booting with Windows.

Tried the following:
[LIST]
[*]Do not connect to WiFi
[*]Disable update installation
[*]Disable 3-rd party package installation
[*]Adding 'nomodeset' or 'nouveau.modeset=0' (as suggested [here]("http://askubuntu.com/questions/760934/graphics-issues-after-while-installing-ubuntu-16-04-with-nvidia-graphics")) to kernel command line.
[/LIST]

Unfortunately none of this solved the issue, the installer still crashes:(. When I add 'nomodeset' or 'nouveau.modeset=0' to the command line, the crash is followed by a LiveCD desktop, rather than a terminal screen with error messages.
Does anyone have any other ideas?

---

### Post by oldfred on 2016-10-13
Some other threads specific to that model, but Intel chip?

 Ubuntu 16.04 on Dell Xps 15 9550 (i7-6700HQ - 1TB SSD - UHD 4k touch)
[http://ubuntuforums.org/showthread.php?t=2317843](http://ubuntuforums.org/showthread.php?t=2317843)
Dell Xps 15 9550  Ubuntu 15.10 on new Infinity display (i7 6gen 16gbr UHD 4k touch) post 272 says 16.04 good
[http://ubuntuforums.org/showthread.php?t=2301071](http://ubuntuforums.org/showthread.php?t=2301071)
[http://ubuntuforums.org/showthread.php?t=2301071&p=13447241#post13447241](http://ubuntuforums.org/showthread.php?t=2301071&p=13447241#post13447241)

---

### Post by sergeip2 on 2016-10-14
Solved. Display drivers appear to be a red herring. There were actually two different issues here:
[LIST=1]
[*]In the laptop's UEFI settings, the SATA mode of the SSD drive was set to RAID instead of AHCI. This means ubiquity's partition manager cannot edit partitions.
[*]Instead of displaying a message about the AHCI issue, the partition manager dialog just crashes with a null reference exception. This is what causes the error dialog ("Ubuntu is experiencing an internal error...").
[/LIST]

The solution was to change the SATA mode to AHCI.

---

### Post by mörgæs on 2016-10-14
Thanks for posting the solution. Please read Bucky's signature.

---

### Post by Bucky Ball on 2016-10-14
> **mörgæs said:**
> Thanks for posting the solution. Please read Bucky's signature.

+1 to both. Blue link, last line of my signature at the bottom of this post, and well done. :)

---

