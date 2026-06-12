---
title: "Unetbootin HDD install, how to install GRUB?"
date: 2011-09-19
forum: Installation &amp; Upgrades
---

### Post by mikeym on 2011-09-19
hi,

I'm trying to install a ubuntu server on a machine that has a few eccentricities. It doesn't have a working CDROM and the USB is knackered so I can't use a USB stick. I'm trying to use UNetBootIn's HDD install option to put it on a hard disk temporarily plugged into a working computer then swap it over and use it to install. AS I understand it UNetBootIn will just install the image to the disk and I need to run grub to change to boot record on teh disk so it will boot.

Does anyone have any idea how to go about this?

---

### Post by An Sanct on 2011-09-19
As far as I know, you can install Linux on a drive on another machine and then swap the drive to the computer without an optical drive and USB support (almost like a live install)

Be careful that you know if you need an 64bit or 32bit distribution.

---

### Post by Hakunka-Matata on 2011-09-19
unetbootin installs a syslinux MBR on my install usbs, cds
It will boot if it's selected as the first boot drive in BIOS

---

### Post by ajgreeny on 2011-09-19
It should be a lot easier on a server with presumably an ethernet connection, not wireless, and with no need for graphics drivers, etc etc.

Just put the hard disk into another machine, install the server OS, making sure grub goes on the root of the server drive, not the first drive on the machine you are using to install the OS, if it has its own drive still attached.

As most, if not all of the configurations needed to boot now work with UUIDs, ie grub and fstab, there should be few if any problems, and it should boot straight away in the original machine.

---

### Post by mikeym on 2011-09-20
OK, I was solidly at this till 2 in the morning yesterday, still no success. 

Thanks for the suggestions they gave me the closest to success. So here's what I've tried:

Formatting the transferable drive as etx3. Mounting the Ubuntu sever ISO copying with *cp -R /media/LiveISO /media/TransferableDrive* then installing grub on the drive with *sudo grub-install --root-directory=/media/TransferableDrive /dev/sdc*

I was able to boot the drive and begin the install but when I got to check and mount the CDROM it wouldn't mount. I got past this install step by mounting *mount /dev/sdb1 /cdrom* however I then got stuck at the installation stage where it said it was unable to determine the release.

So, I tried installing using UNetBootIn and selecting USB and "show all drives" then selecting my transferable HD. It installed the files and Grub as though it were a USB. I tied booting from the disk but it was not recognised as a bootable drive.

So I took the drive with the USB stuff on it and tried *sudo grub-install --root-directory=/media/TransferableDrive /dev/sdc* to install GRUB. This made the drive boot and I tried the install but it failed when it tried to mount and detect the CDROM. This time mounting it manually did not allow the install to proceed.

So I tied a PXE boot from my working computer. This gave me a grub boot screen but I realised that it only allows you to install the Desktop version not the server. I tried following a few notes I could see on how to make a PXE boot install the sever but none seemed to work without major reworking that I was not able to figure out.

So I followed advice here and installed from a USB onto the transferable drive on my Ubuntu Desktop machine then transferred the disk to the new server. I was able to install but when I boot of the transferred drive on the server it seems to be a broken install. It can't comes up with an *inotify* warning saying it cant find /dev/sda5 which it wouldn't as this machine doesn't have one and the transferred drive is /dev/sdb. It then can't find /boot. I can manually recover by  running *mount /dev/sdb1 /boot* then pressing [ctrl]+D to continue the boot and boot in. But i don't know how to fix these problems.

---

### Post by mikeym on 2011-09-20
OK, I think I'm going to proceed with the "broken" install as it's not as bad as I thought. A quick fix of /etc/fstab to point to /dev/sdb rather than /dev/sdd (which it was on the Desktop) and it not finds /boot and therefore the LVM partitions. 

There is a separate bug about LVM (possibly APCI) and booting that gives off the inotify warnings:

[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/581566](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/581566)

I've installed cryptsetup for now as the workaround.

Now I need to figure out how to get my eth0 built in ethernet card to work.

---

### Post by mikeym on 2011-09-20
OK, things just got _a lot_ easier. 

I managed to get networking working so I decided to look up my BIOS as the problems I was having were ACPI problems as was always the problem with this motherboard. I found that there was a new update, formatted a partition on one of the drives as Fat32 put the BIOS update on it and flashed it.

I now have working USB on the server motherboard! 

I'm going to reinstall off the USB on the server now. :D

---

### Post by An Sanct on 2011-09-20
Great! :)

---

