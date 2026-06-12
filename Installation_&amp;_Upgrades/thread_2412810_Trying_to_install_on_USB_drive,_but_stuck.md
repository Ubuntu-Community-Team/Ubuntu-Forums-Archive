---
title: "Trying to install on USB drive, but stuck"
date: 2019-02-17
forum: Installation &amp; Upgrades
---

### Post by gabiarzu on 2019-02-17
Hi guys, i was following a online guide on linuxhint on how to install a bootable drive from the USB drive. 
- so i installed ubuntu using rufus and everything went fine so far.
- got ubuntu to boot, and found the install button.

my issue that after the step of "Updates and other software" i got no page i could choose the type of install, instead im going straight to a page where i choose the partition but its empty, and "new partition" and "revent" buttons are gray.
the only buttons i can press are change (which crashes the install) and the usual quit, back or install.

how can i proceed? i want to install it on the USB without compromising my windows.

thank you.

---

### Post by yancek on 2019-02-17
Most likely explanation is that you left windows hibernated so you need to turn off hibernation/fastboot and anything related before trying to install Ubuntu if you have windows 10.  If you have some other version of windows, you will need to indicate that.  You also need unallocated space on which to install Ubuntu which means using the windows Disk Management tool to shrink the largest windows partition.  AFter doing that, you should boot windows and run chkdsk to verify it boots and has no problems with the filesystem.  Dual booting windows 10 and Ubuntu is explained at the Ubuntu documentation site at the link below.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2019-02-17
In addition to yancek's suggestions, it is better to partition in advance with any install to any second or external drive. And then use Something Else install option.

For UEFI you will want an ESP - efi system partition (FAT32) on the external drive, but Ubuntu's default install will normally use ESP on first drive seen usually sda or first NVMe drive.

If you can disconnect first drive or turn it off in UEFI settings so only drive you want to install into is seen that also then works.

       Install Ubuntu in UEFI mode on second HDD without affecting first HDD
[http://ubuntuforums.org/showthread.php?t=2305876](http://ubuntuforums.org/showthread.php?t=2305876)
[https://askubuntu.com/questions/786986/boot-ubuntu-from-external-drive/942312#942312](https://askubuntu.com/questions/786986/boot-ubuntu-from-external-drive/942312#942312)
[URL="http://askubuntu.com/questions/591193/install-ubuntu-alongside-win-8-1-on-separate-physical-drives-and-dual-boot"]http://askubuntu.com/questions/591193/install-ubuntu-alongside-win-8-1-on-separate-physical-drives-and-dual-boot
[https://ubuntuforums.org/showthread.php?t=2192378](https://ubuntuforums.org/showthread.php?t=2192378)
[/URL]

---

### Post by gabiarzu on 2019-02-20
im sorry, i might have not been clear enough. im not trying to install it on the computer, since i dont wanna deal with anything on the laptop itself. 
all im trying to do is to use ubuntu exclusively from the usb drive, and by following the guides i was aware that i needed to install it after booting into it.
the problem i face is that the install process wont let me choose the usb drive to install on it.

have i understood something wrong?

---

### Post by oldfred on 2019-02-20
The links to install to second drive are for either internal or external.
Your USB flash drive will be seen as an external drive.

If SSD & USB3 it will work well. But if USB2 and flash drive, it will be somewhat slower booting & reading files and very slow doing writes.

Full install to USB3 flash drive took me over 40 minutes. Internal install to SSD even with updates checked is less than 10 minutes. 
I was a bit surprised as I have an old slower SATA SSD and plugged it in with an adapter to USB3 and it was only somewhat over 10 minutes to install. Just about same time an install to my HDD as sdb takes.

---

