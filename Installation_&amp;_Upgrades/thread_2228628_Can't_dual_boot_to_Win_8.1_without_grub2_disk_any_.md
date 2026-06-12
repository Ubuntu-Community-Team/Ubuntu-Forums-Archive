---
title: "Can't dual boot to Win 8.1 without grub2 disk any more"
date: 2014-06-08
forum: Installation &amp; Upgrades
---

### Post by bishop_ on 2014-06-08
Hi everyone,

I am attempting to set up my new computer to boot to Windows 8.1 or Ubuntu 14.04.

I have a 128 GB drive that Windows is installed on and a 64 GB one I would like to use for installing Ubuntu.

I downloaded the Ubuntu install disk, burned it, booted to it and ran the install program installing onto the 64 GB drive.

It did not recognize my Windows installation but I followed the steps in the following guide to install Ubuntu for dual-boot anyway:

[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)

However, unlike in the guide, after install completed and I rebooted, my machine now boots directly to Ubuntu with no grub or other OS selection menu appearing.

I downloaded and burned the Super Grub2 Disk ([http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)) and booted with it in my CD drive, and it finds both my Windows and Ubuntu installations (in fact it shows me 8 separate OS entries, the working Windows and Ubuntu entries, plus a bunch of Ubuntu entries which mostly don't work, saying something about a panic when I select them, and a second Windows entry that gives an error message about needing to repair my installation from the Windows installation disc, both of the Windows 8.1 entries showing as Windows Vista).

I also get a nasty sounding message I guess from my bios about an unauthorized rewrite of some kind of firmware when I boot with Super Grub2 Disk before I get to the menu.

I tried restoring my grub with this guide:

[http://www.supergrubdisk.org/wizard-restore-grub-with-super-grub2-disk/](http://www.supergrubdisk.org/wizard-restore-grub-with-super-grub2-disk/)

My fdisk output shows all 5 of my hard disks (the 2 SSDs I have the OSes installed on, another SSD for games, and two HDDs for data).

It lists /dev/sde, my Ubuntu SSD, as my boot drive.

When I ran "grub-install /dev/sde" it reports "Installation finished. No error reported." as expected, but the state of my system is unchanged - I still get no OS selection menu and go straight into Ubuntu when I reboot unless I use the super grub2 disk.

What should I do to get my boot sectors/grub/OS selection straightened out?

Many thanks!

---

### Post by oldfred on 2014-06-09
Did you convert installs to BIOS with MBR.
Fdisk should not work if you have UEFI as that has to have gpt partitioning.

Run the BootInfo report and post link. 
I also thought some versions of Super grub ran the bootinfoscript also which is the same as the first part of BootInfo report?

Do not run auto fix, as that installs grub to the MBR of every drive and you only want that in the MBR of your Ubuntu drive.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

