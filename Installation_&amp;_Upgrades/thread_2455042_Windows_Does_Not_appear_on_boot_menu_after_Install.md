---
title: "Windows Does Not appear on boot menu after Installing 3"
date: 2020-12-11
forum: Installation &amp; Upgrades
---

### Post by andodeki on 2020-12-11
l have installed 3 ubuntu 20 version in different hdd partions each in it's own partion including Windows 10 but I can't see it(windows 10) in my Boot Menu but I can see other ubuntu installed. I run sudo os-prober and sudo update-grub but I can't see the Win 10 in grub too even when I reboot too.

Below is a boot-repair link which I did also but no win 10 in boot menu.

[http://paste.ubuntu.com/p/mDFdDHhXVn/](http://paste.ubuntu.com/p/mDFdDHhXVn/)

---

### Post by yancek on 2020-12-11
I don't know what changes might have been made but, your system is a Legacy/MBR install of all the Ubuntu install and the windows partition is on a logical drive.  sda1 is an Extended partition and all drives labelled sda5 and higher are logical drive.  Windows is on sda5, which is a logical partition and there is no primary partition with its boot files so it will not boot.  Was this originally and EFI install?  I don't know how windows installer would put its files on a logical partition.  Is this an upgrade from an earlier version like windows 7?  Did you delete any windows partitions?  Your boot repair output does not show complete grub.cfg files from any of the Ubuntu partitions.  If you go to /boot/grub/grub.cfg do you see a menuentry for windows?  Do you see a windows entry in either of the other grub.cfg files on the different partitions (sda6 and sda9)?  

Even if you had a boot entry for windows in one or all of the grub.cfg files, it would not boot because there are no boot files for windows on a primary partition.

---

### Post by oldfred on 2020-12-12
Somehow you converted the original sda1 which was the Windows boot partition to an extended partition.
Windows only boots from a primary NTFS partition with the boot flag. You are missing the two essential boot files that must be in a primary partition. Most Windows installs have a smaller sda1 as boot partition and main install or c: drive as sda2. Then you may have another primary or start having the extended partition wtih many logical partitions.

Vista/7/8/10 BIOS (with 7, 8 or 10 the first two files are usually in a separate 100MB boot partition)
[COLOR=#ff0000]/bootmgr /Boot/BCD[/COLOR] /Windows/System32/winload.exe 

You can only have one extended partition so it does not look like it will be easy to reorganized partitions to have a primary NTFS partition for Windows to boot from.  The current NTFS is in the middle of the extended partition.  You may be able to convert sda5, 6 & 7 to primary partitions and make the extended be all the rest. Then run Windows repairs from your Windows repair/recovery drive to install bootmgr & BCD to main install. Does not have to have separate /boot partition. But boot flag must then be on the one NTFS partition as primary for repairs to work.

See if this lets you just convert from logical to primary.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

There also is no real reason to have 3 swaps and then all 3 mounted in fstab.

---

