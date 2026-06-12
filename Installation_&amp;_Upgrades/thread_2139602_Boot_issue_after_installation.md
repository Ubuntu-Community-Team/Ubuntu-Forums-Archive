---
title: "Boot issue after installation"
date: 2013-04-27
forum: Installation &amp; Upgrades
---

### Post by b0wter on 2013-04-27
Hey,

with the release of 13.04 I decided to give Ubuntu a try and I've run into some serious problems so far.
I am running a pc (EFI) with two hdds, one of them contains Windows 7, the other one Linux Mint.
So what I tried was create a bootable usb stick to install Ubuntu. The creation worked flawlessly (been using unetbootin). During the installation the installer asked me where to install and I selected the option to replace Linux Mint.
While installing I ran into the infamous [Squashfs error]("https://help.ubuntu.com/community/SquashfsErrors") (md5 checksum of the ISO was okay). So I used another tool (rufus) to create the usb stick, which worked fine. When I ran the installer it only offered me the option to either replace Windows 7 or install Ubuntu alongside. I chose the later thinking that I was able to select that the installer would install Ubuntu alongside Win7 on the **second** hdd. But that maniac installer simply tried to push Ubuntu onto the same drive as windows by reducing the windows partition by 16GB (the partition has had a free space of 5GB!!!). So I guess that Windows installation is gone for good >:[
The installtion didnt work out, I ran into the sqashfs error again....
That was where I got to a second Ubuntu machine and created a bootable USB stick with the Startup Disk Creator. Since I was already bugged enough I simply disconnected the windows hdd and ran the installer from the USB stick. It worked flawlessly this time but after rebooting Ubuntu wouldn't boot. I simply get a blank screen with a blinking cursor.
So what I have now is a hdd with a probably broken installation of Windows 7 (including the "old" GRUB bootloader from the Linux Mint installtion) that boots into Grub rescue mode and a second hdd that should contain Ubuntu but does not boot at all. Does anyone have any advice on how to advance from here on? I simply want to install Ubuntu on my second hdd and get Windows back to work (preferably without reinstallation).

edit: I have no idea what I did different this time but I tried again and managed to install and boot Ubuntu successfully by disconnecting the windows hdd from the mainboard. Still the issue remains on how to continue from here on...

---

### Post by dino99 on 2013-04-27
some usb thumb have a borked partition table; so with gparted or partedmagic, rebuild the table first, then format as Fat32

---

### Post by p-dh on 2013-04-27
I have also had problems with USB partitions of 4 GB or more. Once I changed to a 2GB partition, everything worked as expected.

Peace,
Paul :cool:

---

### Post by b0wter on 2013-04-29
Thanks. I finally got it working again, yesterday evening.
I used an alternate USB stick for the successful installtion of Ubuntu. Afterwards I tried to correct the MBR on the windows partition with the Windows 7 DVD by booting into the recovery console and using bootsec but to no avail. The solution was much easier in the end... I connected both hdds, booted the Ubuntu partition performed a simple "update-grub" and told EFI to always boot my second hdd (containing Ubuntu).  Works fine now.

---

