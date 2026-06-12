---
title: "Notebook with Ubuntu - how to partitioning with Windows?"
date: 2016-09-04
forum: Installation &amp; Upgrades
---

### Post by leokelba on 2016-09-04
Hello guys,
I bought a notebook of 1TB with Ubuntu installed in just one partition of the HD. I wanted to install Windows too. I realised that it is possible to create a partition of the HD where I can reach the files through Ubuntu or Windows. How can i do that?
I've already done a boot pen-drive. with Windows 10. I didn't have installed yet cause I couldn't allocate HD from inside Ubuntu. And I wanted to do that with this possibilitie pf acess the files from both Ubuntu or Windows.

Thanks very much!

---

### Post by gordintoronto on 2016-09-05
In my experience, the only way to dual boot is to install Windows first, then Linux. During the Windows installation, you should be able to tell it how much of the hard drive to use. Since it's probably formatted as EXT4, Windows will think it is empty.

Ubuntu will be able to access the Windows files, but for Windows to access the Ubuntu files, you would need to install a driver.

---

### Post by yancek on 2016-09-05
If your Ubuntu was pre-installed, the partition(s) it uses will likely take up the entire drive the same way a pre-installed windows system does.  You can get and post information on that by opening a terminal in Ubuntu and entering the following Command:  sudo fdisk -l

If you want to partition, you will need to use some Linux on a Live CD or flash drive or get the GParted partition manager and burn it to a CD and boot from it.  GParted will not resize a partition which is mounted so installing it to your Ubuntu system would not work.  The GParted site where you can download it is at the link below.  The second link is the entire GParted Manual which explains how to shrink a partition, create and format as well as a number of other options.

 [http://gparted.org/download.php](http://gparted.org/download.php)

[http://gparted.org/display-doc.php%3Fname%3Dhelp-manual](http://gparted.org/display-doc.php%3Fname%3Dhelp-manual)

It is usually not a problem to access files on windows from Linux as long as you have ntfs-3g installed.  I don't think you can do it from windows without third party software installed.

You can install windows on a drive with another OS.  Have you test booted the windows 10 usb to see if it boots?  You need to be familiar with device/partition naming conventions in windows and you will also need to select the Custom option in the windows install or you will overwrite everything.  The first thing you need to do is to shrink the Ubuntu partition to whatever size you want and either leave unallocated space on which to install windows or format it ntfs.  Make sure the partition is a primary partition and has the boot flag set which you can also do in GParted.  Don't have any other drives plugged into usb ports as the installer seems to get confused, at least that happened in my case and maybe your luck will be better.

I installed windows on a system with a number of other Linux systems already installed and it was successful.  I had to reinstall Grub  so you will need to reinstall the Ubuntu Grub bootloader so I hope you have an Ubuntu DVD/flash drive.  You might do an online search for install windows when Linux already installed.  Another very important factor is whether your current Ubuntu is using UEFI.  If so, you need to install windows UEFI.  The install I did was MBR.

---

