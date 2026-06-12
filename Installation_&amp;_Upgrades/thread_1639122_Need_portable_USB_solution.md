---
title: "Need portable USB solution"
date: 2010-12-06
forum: Installation &amp; Upgrades
---

### Post by DALEKMOS on 2010-12-06
I will start off by saying that the only experience with Ubuntu I have is through fooling around with a live USB of 10.04 for a day and installing WINE on it.

I was wondering how I could turn my 8GB flash drive into a portable Ubuntu 10.04 live USB that I can install applications onto without later re-installation. For example, I could go to a friends house and play games by booting Ubuntu from the device and using WINE to run the games which too would be installed on the drive. I don't really understand how I would go about it. Do I split the drive into separate partitions, or is this the whole point of persistence? (it is my understanding persistence was for system changes)

Any help would be much appreciated thanks!

---

### Post by oldfred on 2010-12-06
With 8GB you have room for a full install. Persistence does not let you install upgrades, just save data.

It now may be better to unplug hard drive if you can as the Maverick installer only lets you choose where to install grub if you use manual partitioning. Grub likes to install to sda, or your internal drive which then causes problems.
You also do not want to install any video drivers as you want the most generic possible. And possibly know how to add parameters to the grub boot line to change video modes.

Standard full install to flash or SSD:

See post #19 C.S.Cameron ( But I do not unplug hard drive, just use advanced button to install to USB)
Maverick now only gives combo box on grub location if you use manual install.
[http://ubuntuforums.org/showthread.php?t=1509603](http://ubuntuforums.org/showthread.php?t=1509603)

It does not have to be encrypted:
Standard full install to flash or SSD:
Ubuntu Karmic Koala Encrypted Flash Memory Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
Use ext2 or ext4 without journal
tune2fs -O ^has_journal /dev/sda1
No swap or set swapiness
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler

On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
* Older Intel video card: i915.modeset=1 or i915.modeset=0
* nVidia: nomodeset
* Generic: xforcevesa or nouveau.modeset=0
* Radeon: radeon.modeset=0

Or something like this:
Create Portable Ubuntu for 2 different Video Cards - script
[http://ubuntuforums.org/showthread.php?p=8107778](http://ubuntuforums.org/showthread.php?p=8107778)

---

### Post by DALEKMOS on 2010-12-06
Thanks, this looks like what I'm looking for. 4GB sure is a lot of space to be taking up though.

---

### Post by DALEKMOS on 2010-12-06
Thanks for all the support! You helped me with my problem.

---

### Post by C.S.Cameron on 2010-12-07
> **DALEKMOS said:**
> Thanks, this looks like what I'm looking for. 4GB sure is a lot of space to be taking up though.

You can make a more compact persistent disk image install using usb-creator from the Live CD or Universal fromPendriveLinux.com

---

