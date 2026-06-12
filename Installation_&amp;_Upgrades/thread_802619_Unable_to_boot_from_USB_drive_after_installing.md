---
title: "Unable to boot from USB drive after installing"
date: 2008-05-21
forum: Installation &amp; Upgrades
---

### Post by humbll on 2008-05-21
Hi all,

I have a problem with installation of latest Ubuntu release on a USB flash drive. I installed it to the drive, but when I try to boot it up I get the error: ERROR LOADING OPERATING SYSTEM. (Before GRUB loads)

This happens because I have another USB drive connected, an external Seagate 250GB. When I turn it off and boot up, the GRUB loader comes up and I tell it to boot Ubuntu, at which point it tells me the drive does not exist, presumably because the drive ID's have been altered due to the absence of the Seagate I turned off. 

Does anyone have ideas on how to work around this? I would preferably like it to boot up regardless of what other devices are or are not connected to my computer at any given point..

Below is a dump of the fdisk -l from terminal in live disk - Thanks in advance.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 38.5 GB, 38502535680 bytes
255 heads, 63 sectors/track, 4681 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc14dc14d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2301    18482751    c  W95 FAT32 (LBA)
/dev/sda2            2302        4680    19109317+   7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000f7be

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    7  HPFS/NTFS

Disk /dev/sdc: 4060 MB, 4060086272 bytes
255 heads, 63 sectors/track, 493 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         465     3735081   83  Linux
/dev/sdc2             466         493      224910    5  Extended
/dev/sdc5             466         493      224878+  82  Linux swap / Solaris
ubuntu@ubuntu:~$

---

### Post by humbll on 2008-05-21
Here is some more info:

When I go to the GRUB loader, hit "E" and it shows this info:

ROOT (hd2,0)
Kernel (/boot/vmlinux----etc) **UUID 3f7fd3206ffs-4585**

I find that grub is also not able to boot windows, when attempted the error:

GRUB ERROR 13 Invalid or unsupported executable format.

When I boot normally without using grub (which I opted to install on the USB flash drive) windows will boot up normally.

---

### Post by humbll on 2008-05-21
I ran across this:
[http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/](http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/)

And I am off to try it now, I guess Ubuntu cannot just be insatlled directly to the flash USB drive directly as I did it since the instructions on that page guide you though a bunch of other steps. .

---

### Post by Rallg on 2008-05-21
I have a different Linux distro that can boot from pendrive via GRUB. My Ubuntu is on the hard drive, and can only be booted (by intent) via USB GRUB when it is inserted and selected at boot time.

I discovered that GRUB (I use Grub4DOS) thinks that hd0 is wherever it is located. In my own case, GRUB thinks that hd0 is the USB, and hd1 is the hard drive.

That info may or may not help you. But it is a common problem.

Incidentally, a USB is not bootable unless you make it bootable (for example, using HP boot software). I don't know if the GRUB install can do that for you.

---

### Post by humbll on 2008-05-22
Ok, I am officially lost here. I tried to do the persistent installation I linked to in the third post in this thread, and when I boot up I instantly get error 17 before I even get grub loaded.. 

I also found that my original installation to the USB drive is, in fact, a legitimate way to install the Ubuntu OS onto a flash drive, as detailed [here]("http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/"). It should have worked the way I did it. So if any of you have any idea why my original install direct to the flash drive as described in posts #1 and #2 in this thread did not work correctly, please enlighten me.

 It is interesting to note that the fdisk -l output my drives are all sd - as in sda sdb etc.. but when I got to the grub menu and pressed "E" they were all listed as hda hdb etc.. attempting to alter them to sda or sdb would result in an error..

Anybody??

---

