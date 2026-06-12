---
title: "Installed full version 2 usb hdd problems"
date: 2011-01-10
forum: Installation &amp; Upgrades
---

### Post by itzzkolby on 2011-01-10
I installed Ubuntu on to a usb hard drive now without that hard drive plugged in i cant get to my windows(it goes to grub recovery). With it plugged in it lets me pick witch OS to use. How do I get it to just boot right to windows when its not plugged in?

---

### Post by oldfred on 2011-01-10
You need to install grub to the external drive's MBR and a windows boot loader to the internal drive's MBR.

When you installed Ubuntu to the external, you had to use advance/manual install to give you the option on where to install grub2's boot loader. 

Boot Ubuntu and install grub to whatever drive the external is called, probalby sdb but you have to check as some systems make drives different order.

reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub
to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

then we want to install the lilo boot loader to the MBR. Lilo works jsut like windows from the MBR in that it looks for the partition with the boot flag to find more code to continue booting. We will not install lilo (just MBR part) as we are using windows to boot.

Restore basic windows boot loader - universe enabled
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

Set BIOS to boot external first and that will give you grub, If external not found lilo will boot windows.

---

