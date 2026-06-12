---
title: "&quot;loading operating system&quot; halt"
date: 2011-01-11
forum: Installation &amp; Upgrades
---

### Post by ale_login on 2011-01-11
Hi all,
I'm stuck with a very annoying problem installing Ubuntu Server 10.04. After all the installation procedure I reboot and the system immediately halts saying "Loading Operating System..."

The config. is:
AMD Phenom II X4 955
Gigabyte 880GMA-UD2H
2x2Gb DDR3-1333 ram
500Gb sata 3.0 hdd
NO cd drive.

I installed from a USB stick selecting to boot from USB_HDD. Then I partitioned as follows:
256Mb /boot
remaining LVM with 8Gb swap and 16Gb root

I repeated the installation 3 times, and the only way I can now boot into the operating system is leaving the USB stick in and selecting again to boot from USB-HDD.
But when I type "df" from the console, I actually read 16Gb (which means I'm on the hard drive!)

I'm totally confused...

---

### Post by ale_login on 2011-01-11
I forgot to mention:
I never see the GRUB menu, not even when it loads from the USB stick.

---

### Post by ale_login on 2011-01-11
I solved the problem:
apparently, and for no evident reasons, the installation was writing the MBR on the USB stick.
I had to make a live usb with the Desktop ubuntu edition and reinstall GRUB from there.

---

