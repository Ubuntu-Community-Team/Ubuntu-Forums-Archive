---
title: "Boot Ubuntu without effect Windows MBR"
date: 2012-02-17
forum: Installation &amp; Upgrades
---

### Post by Coastalguy on 2012-02-17
Is there a way, to install Ubuntu, so that it can be booted separately so as to not effect the Windows 7 boot manager? Normally, I will want to boot up to my Dual Boot Windows 7 screen. On occasions, I would like to boot up to Ubuntu directly, without going through the Windows boot up process.

I have a totally clean, external USB drive that I would like to use for Ubuntu.

Thanks,

---

### Post by darkod on 2012-02-17
You can, but if you think it's easier for you to use the motherboard boot menu and select which disk to boot from.
In that case when you install ubuntu on the ext hdd, install the bootloader also on the ext hdd. Windows bootloader will remain on the int hdd.

Then when booting the PC select whether to boot from the int or ext.

---

### Post by drs305 on 2012-02-17
Here is one way. I'll assume Windows is installed on sda (internal), Ubuntu sdb (USB).

Install Ubuntu on sdb and ensure Grub is placed in the sdb MBR. To guarantee it doesn't overwrite the sda MBR, you could disconnect sda during installation if you wish.

The result will be the Windows bootloader on sda, the Ubuntu bootloader on sdb. 

Change the BIOS boot order to boot sdb first, sda second. If the USB is connected, you will get the sdb bootloader (Grub/Ubuntu). If the USB is not connected, you will get the Windows bootloader. Or change the BIOS order when you want Ubuntu.

If you want Windows most times, but don't want to disconnect the USB, you can set Windows to be the default in Grub and still get to your Windows bootloader. You could have the timeout set to 0 or a second or two and it boot to the Windows menu automatically. In this way you would either not see the Grub menu or only see it for a second or two before it continues to the Windows menu.

---

### Post by ajgreeny on 2012-02-17
Don't forget that with ubuntu on a USB disk, it will run much slower than on an internal SATA or even IDE drive, due to the relatively slow drive access times that you will be using.

---

### Post by Coastalguy on 2012-02-18
Thanks, great information.

My Windows is installed on disk0 (sda), internal and I want to install Ubuntu on my USB. As I also have a 2nd internal drive (sdb), I assume the USB will be sdc? 

I also understand it will be slower, but I am only playing with it to learn Linux. I also have a firewire external drive which may be a better bet.

A question, to load Grub2 onto the drive with Ubuntu, is there an option, during the install, that lets you do this, or do you need to disconnect sda to be sure?

Thanks,

---

### Post by ajgreeny on 2012-02-18
There is indeed an option at the bottom of the disk preparation page (I think that's where it is) which will offer a dropdown box with all partitions and disks shown.  Do not put grub onto a partition but on to whatever the dev name (/dev/sdb) for your USB disk is shown as.

In order to be able to do this **YOU MUST CHOOSE "Something Else"** at the disk preparation stage. If not everything will end up as the default and grub will be on the first disk MBR, just where you don't want it.

---

### Post by gordintoronto on 2012-02-18
See Full Circle Magazine, issue 47, page 35.

---

