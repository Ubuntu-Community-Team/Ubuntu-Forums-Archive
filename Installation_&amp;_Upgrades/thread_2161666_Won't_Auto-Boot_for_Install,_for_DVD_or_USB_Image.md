---
title: "Won't Auto-Boot for Install, for DVD or USB Image"
date: 2013-07-11
forum: Installation &amp; Upgrades
---

### Post by Sethalos on 2013-07-11
Greetings.

I had Ubuntu 13.04 installed on my Media computer, however, after an update two days ago-ish Ubuntu just crashed and I wasn't able to do anything with it. So, I decided to re-install and just start over. Now I can't get the disk to auto-boot it just keeps going to the current broken install. Same deal with the USB Pendrive image, it just goes right on past to the broken install.

Things I've done:

1) Yes...I made sure that the boot order was proper in the BIOS.
2) I successfully installed Mint 15 (no boot issues there) and then tried to re-install Ubuntu...no luck, continued right on to the Linux Mint install.
3) Re-downloaded another image, checked the MD5, and tried again...no luck.
4) Created another Pendrive image on USB stick....no luck
5) Checked to see if the Processor had PAE support (pretty sure that's it)...and it does.
6) Tried a flame thrower on the computer out of frustration...crap, need a new computer.

So, any help or advice to get this to boot onto my system again would be appreciated.

Thanks.

Seth.

---

### Post by sudodus on 2013-07-11
How did you install Mint 15? Do you want Ubuntu alongside with Mint? Is there space enough for it? Is it possible to create new partiitons? Use the same method as for Mint! (for example CD/DVD/USB).

Normally I prepare the partiitons with ***gparted*** when running a live session booted from the install drive. Then when running the installer, I select ***Something else*** at the partitioning page, and select the partiiton intended for Ubuntu as the root partition.

I would also decide if I want Ubuntu to manage grub (or in your case to let Mint continue doing it). If I do *not* want Ubuntu to do it, I will change the target for the bootloader (typically to the partition where Ubuntu is to be installed; where it will not be used). After installation I need to remember to run sudo update-grub in Mint to make it find Ubuntu.

-o-

If you have four primary partitions in an MSDOS (MBR) partition table, you need to delete one of them to make it possible to create an extended partition, and in that partition you can create many logical partitions. Normally you would need two partitions for Ubuntu, one root partition and one swap partition, but you should already have a swap partiiton (created for Mint).

---

### Post by Sethalos on 2013-07-11
> **sudodus said:**
> How did you install Mint 15? Do you want Ubuntu alongside with Mint? Is there space enough for it? Is it possible to create new partiitons? Use the same method as for Mint! (for example CD/DVD/USB).

Normally I prepare the partiitons with ***gparted*** when running a live session booted from the install drive. Then when running the installer, I select ***Something else*** at the partitioning page, and select the partiiton intended for Ubuntu as the root partition.

I would also decide if I want Ubuntu to manage grub (or in your case to let Mint continue doing it). If I do *not* want Ubuntu to do it, I will change the target for the bootloader (typically to the partition where Ubuntu is to be installed; where it will not be used). After installation I need to remember to run sudo update-grub in Mint to make it find Ubuntu.

-o-

If you have four primary partitions in an MSDOS (MBR) partition table, you need to delete one of them to make it possible to create an extended partition, and in that partition you can create many logical partitions. Normally you would need two partitions for Ubuntu, one root partition and one swap partition, but you should already have a swap partiiton (created for Mint).

Hiya,

Thanks for your reply.  1) So I did a clean install of Mint 15, it auto-booted properly without issue. 2) I don't get the live session, the distro won't auto boot, it completely bypasses the DVD or Pendrive, in other words I put the DVD in reboot the system, and even though my BIOS is set up to boot from DVD first, it completely skips it and just goes to the hard drive, as if it's not seeing the boot up script off the DVD. This is the same with the Pendrive.  Now when I tried Mint 15, it just worked. Located the disk, booted into the live session, and I installed it from there. With the Ubuntu DVD/Pendrive, it completely ignores the DVD/Pendrive.

So my issue is really that I just can't get my system to recognize the Grub off of the boot disks/drives. Any other Distro's work like a charm. So far I've successfully installed, Magei, Bodhi, and Mint 15. Without any issues at the boot screen, they load and run fine off of the DVD. Ubuntu 13.04 for some reason just won't auto-boot.

---

### Post by sudodus on 2013-07-11
I understand what you write, but I don't understand why it is like this. We (I and other people) who might help you, need to know more.

Please post the specs of the computer: Brand name, model, cpu, ram (size), graphics chip/card

Flavour of Linux Mint (it is version 15). Flavour of Ubuntu (standard with Unity or ...)? 32-bit or 64-bit?

Settings in BIOS (UEFI, ...)?

Try to remember if something changed, when Ubuntu 13.04 stopped working (something else than an update)! And try to remember how you installed Ubuntu the first time: Upgrading from 12.10 or a fresh install of 13.04?

---

### Post by Sethalos on 2013-07-11
> **sudodus said:**
> I understand what you write, but I don't understand why it is like this. We (I and other people) who might help you, need to know more.

Please post the specs of the computer: Brand name, model, cpu, ram (size), graphics chip/card

Flavour of Linux Mint (it is version 15). Flavour of Ubuntu (standard with Unity or ...)? 32-bit or 64-bit?

Settings in BIOS (UEFI, ...)?

Try to remember if something changed, when Ubuntu 13.04 stopped working (something else than an update)! And try to remember how you installed Ubuntu the first time: Upgrading from 12.10 or a fresh install of 13.04?

Ok:

1) Asus Laptop: I7 Intel, Nvidia Geforce GT 630m, 16megs RAM
2) BIOS Settings have never been changed, for the exception of Boot Order.
3) Mint 15 Gloria 32 Bit Cinnamon, Ubuntu 13.04 (Fresh install (first time, and attempted reinstall), The issue started after my Ubuntu 13.04 install crashed right after the reboot of a System Update. No changes from my original install of 13.04 to my attempt to reinstall it. Exact same computer configurations for all installs.

---

### Post by sudodus on 2013-07-12
Thank you! One more small question. Is your Ubuntu system 32-bit or 64-bit?

Since Mint 15 32-bit works so well to install and run, Ubuntu 32-bit should work too, at least the boot drive should boot and  not skip to the installed system. But on the other hand, with those computer specs, it should be an advantage to run a 64-bit version of Ubuntu (guessing you mean 16 GB RAM).

Could there be a problem with RAM (that a particular bad memory location is activated by Ubuntu but not Mint)? Try checking with memtest (from the boot menu).

Or is it a problem with the graphics, that you need some boot option or proprietary driver for the nvidia card? But if you cannot even boot, it is not easy to activate any boot option or proprietary driver.

-o-

In your situation I would test along two tracks (you can have a multi-boot setup)

1. Ubuntu 12.04 LTS or 12.04.2 LTS. If the long time support version works for you, it will give you a smooth ride until April 2017.

2. Ubuntu 13.10 alpha. If this version can boot and give you good graphics, it might be the best choice, although it might break a few times, when new packages are not quite compatible with each other. Of course, when released in October, it will get more reliable.

---

### Post by Sethalos on 2013-07-12
> **sudodus said:**
> Thank you! One more small question. Is your Ubuntu system 32-bit or 64-bit?

Since Mint 15 32-bit works so well to install and run, Ubuntu 32-bit should work too, at least the boot drive should boot and  not skip to the installed system. But on the other hand, with those computer specs, it should be an advantage to run a 64-bit version of Ubuntu (guessing you mean 16 GB RAM).

Could there be a problem with RAM (that a particular bad memory location is activated by Ubuntu but not Mint)? Try checking with memtest (from the boot menu).

Or is it a problem with the graphics, that you need some boot option or proprietary driver for the nvidia card? But if you cannot even boot, it is not easy to activate any boot option or proprietary driver.

-o-

In your situation I would test along two tracks (you can have a multi-boot setup)

1. Ubuntu 12.04 LTS or 12.04.2 LTS. If the long time support version works for you, it will give you a smooth ride until April 2017.

2. Ubuntu 13.10 alpha. If this version can boot and give you good graphics, it might be the best choice, although it might break a few times, when new packages are not quite compatible with each other. Of course, when released in October, it will get more reliable.

Hello again,

So I ran memtest and all was well. No graphic issues, no proprietary driver required.

1) So I downloaded 12.04 and it booted without issue ( have it currently installed)
2) Was not able to boot with the 13.10 alpha, same issue 13.04 gave me.

So I'm quite happy with 12.04 for now and will keep using that until I can figure things out. I really appreciate your help, thanks.

Seth

---

