---
title: "Dell Vostro not booting external USB HDD"
date: 2011-07-10
forum: Installation &amp; Upgrades
---

### Post by MIchaelStephens on 2011-07-10
Good morning, can somebody throw me a lifeline???

I have used Ubuntu for several years and arrival of a new laptop from work has started to give me grief.

I use External USB hard drives loaded with Ubuntu 10.10 and boot these directly from the USB port to give me a system which does not touch the 'work machine' HDD.

Since getting a new Dell Vostro 3500 I have had problems getting the USB HDD to boot. The only way at the moment to get a working system is to boot from CD using SUPERGRUB and then point this to the external hard drive.

The BIOS on the PC is up to date (A10) and the boot order is set correctly and I can see the connected USB drive, but when I try to boot the screen goes blank, a dash appears, it drops a line and stops.

I have removed the internal hard drive and done a fresh install onto the USB drive. This drive works when plugged other laptops, but on the Dell it refuses to boot, even though the BIOS reports the drive is connected. It will only boot via a CD with SUPERGRUB.

USB Flash/key drives boot and run OK. DVD/CD's boot and run OK. The USB HDD will boot when loaded with FREEDOS. BUT it steadfastly refuses to boot directly into linux. 

I have even tried to dual boot the drive using a FREEDOS partition - nothing.

HELP

---

### Post by pikusayantan on 2011-07-10
I am facing same problem with my dell inspiron 1050n.

---

### Post by MIchaelStephens on 2011-07-16
Hi, all I finally got mine to boot..
Booted from LiveCD and partitioned the USB hard drive:
/boot 500 meg ext2, primary, bootable
Swap 4 Gb
/ - 12Gb ext4
/home  rest of the drive ext4

Then installed keeping the above structure.

Success...

Default install was not creating a /boot partition..

---

