---
title: "can updates be done on a USB booted live linux with persistance?"
date: 2020-11-03
forum: Installation &amp; Upgrades
---

### Post by james2b on 2020-11-03
Can updates be done on a live linux USB flash drive booted with persistance? I have a 32 GB Ubuntu Mate 18.04.3 LTS and a 4 GB USB stick with Mint 17.2, both with that persistence option. And when done on one computer, can that same USB flash drive then be put in and booted to with a different computer? One is a 2012 dell with 7, and the other is a 2018 MSI Intel based store parts build system with 10.

---

### Post by TheFu on 2020-11-03
Perhaps.  Use **mkusb** to create the setup. Do not load any proprietary GPU drivers. Stay with the F/LOSS drivers.
I've read that over time, the overly file system with all the updates/patches will start having issues.  Of course, the machines and USB drive have to support booting from the specific USB port and USB flash storage.  They aren't all the same.

I don't know how UEFI or Legacy BIOS differences matter on your machines.

Until you try it, you'll never know.

mkusb has a lot of threads here. The guy behind it is active in these forums.  Plan to get a few practice attempts to learn about the different mkusb installation types.  Took me 3 to understand what the different answers really meant.

---

### Post by C.S.Cameron on 2020-11-03
Updates will quickly fill a Persistent USB's Persistence file or partition. The OS is on a read only ISO9660 partition or on a read only filesystem.squashfs file. When an update is done, new files are added to the casper-rw, writable or home.rw file or partition but the files on the read only file or partition are not removed.
Likewise a upgrade is not possible as the kernel is also read only.

If you want a portable drive that can be reliably updated and upgraded, do a full install to USB see: [https://askubuntu.com/questions/1217832/how-to-create-a-full-install-of-ubuntu-20-04-to-usb-device-step-by-step](https://askubuntu.com/questions/1217832/how-to-create-a-full-install-of-ubuntu-20-04-to-usb-device-step-by-step)

---

### Post by ping-wu on 2020-11-04
plse see:

[https://unix.stackexchange.com/questions/364457/how-to-change-the-boot-kernel-of-a-usb-live-w-persistent-running-kali](https://unix.stackexchange.com/questions/364457/how-to-change-the-boot-kernel-of-a-usb-live-w-persistent-running-kali)

---

