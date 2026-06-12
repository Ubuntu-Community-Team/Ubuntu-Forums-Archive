---
title: "Burn An ISO To Flash Drive"
date: 2016-01-02
forum: Installation &amp; Upgrades
---

### Post by shane_faulkinbury2 on 2016-01-02
I was just wondering if someone has an idea on how to burn an ISO to a USB flash drive?  I have Disk Image Mounter and Disk Image Writer, but can't figure them out!  Can someone please give me some guidance?  :confused:

---

### Post by SeijiSensei on 2016-01-02
If you're trying to create a bootable USB drive from an ISO disk image, use the Startup Disk Creator as described here: [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu)

---

### Post by shane_faulkinbury2 on 2016-01-02
Thanks, I'll check it out!

Well I formatted it to ext3 and can't see it in Files!  Startup Disk Creator sees it, but says 0 bytes available.  Now I'm going to have to go to stupid Windows 10 to format it to NTFS!

---

### Post by Bucky Ball on 2016-01-02
You need to format the USB to FAT32 before using either of these. 

UNetbootin:
[www.unetbootin.sourceforge.net](www.unetbootin.sourceforge.net)

Universal USB Installer:
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

---

### Post by sudodus on 2016-01-03
If you use ***mkusb*** to burn an ISO to a USB flash drive, you need no pre-formatting. It will do all the job for you. See this link: [mkusb](https://help.ubuntu.com/community/mkusb)

From Windows you can use the corresponding tool [Win32 Disk Imager](https://wiki.ubuntu.com/Win32DiskImager/iso2usb)

---

### Post by shane_faulkinbury2 on 2016-01-03
Do you know how to recover my flash drives so I can see them again?

---

### Post by Dennis N on 2016-01-03
> **shane_faulkinbury2 said:**
> Do you know how to recover my flash drives so I can see them again?

Insert flash drive. Using gparted, first select the flash drive in the drive selector (upper right) and then create a new partition table (Devices > Create Partition Table > Choose type). On completion of that step, all space on the drive will be unallocated. Make a new partition within the unallocated space of whatever size & filesystem type you need, like FAT32.

---

### Post by SeijiSensei on 2016-01-03
You can format a device with FAT32 from the command prompt.  Suppose your drive is recognized as /dev/sdb with a single partition, /dev/sdb1.  Then at a prompt type:
```
sudo mkfs -t vfat /dev/sdb1
```
to format it as FAT32 (or "vfat").

---

### Post by shane_faulkinbury2 on 2016-01-03
Thanks guys!  Your advice worked and it's much appreciated!  I used gparted to format the usbs to fat32 and then used Startup Disk Creator to write the iso to the flash drive and everything worked perfectly!  :D

---

### Post by Bucky Ball on 2016-01-03
Great news and thanks for marking as solved. Enjoy! :)

---

