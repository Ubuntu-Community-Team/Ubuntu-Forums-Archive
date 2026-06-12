---
title: "Full installation on 32GB USB"
date: 2017-04-12
forum: Installation &amp; Upgrades
---

### Post by rockinbocky on 2017-04-12
Hi!

I'm trying to install Ubuntu onto my 32gb USB drive with help from another usb which has a bootable ubuntu live version. But I can't seem to get it to install.

I used this guide: [http://ubuntuhandbook.org/index.php/2014/11/install-real-ubuntu-os-usb-drive/](http://ubuntuhandbook.org/index.php/2014/11/install-real-ubuntu-os-usb-drive/)

I first unallocate the USB memory, then create the partitions and then it freezes upon installation where it wount mount sdc1.

"The attempt to mount a file system with type ext4 in SCS13 (0,0,0), partition #2 SDC at / failed"

Any thoughts on how to get this to work. Because my windows laptop is dying together with the emmc drive so a full working Ubuntu on usb would be great.



[IMG]http://i.imgur.com/AyzThgK.jpg[/IMG]

[SIZE=2][IMG]http://i.imgur.com/HLlY99A.jpg[/IMG][/SIZE]

---

### Post by yancek on 2017-04-12
The image you posted shows sda4 as a windows partition on the main hard drive and then shows sdc with it's partition.  Why is there a vfat partition on that drive?  You should just create one ext4 or some other Linux partition and a swap.  I don't see any sign of the install usb, is that showing in the windows you view?  The error indicates it is unable to mount sdc1 with the filesystem type ext4.  sdc1 is a vfat filesystem which you would no use with a Linux/Ubuntu install.

---

### Post by rockinbocky on 2017-04-12
Also that doesn't work, it now stalls at "saving installed packages". Had created 30 gb of ext4 and 2gb of swap.

---

### Post by ubfan1 on 2017-04-12
Assuming this is not for a UEFI machine, where you'd actually want a (small, 300G) FAT partition for bootloaders, I assume your sdc1 is just for file transfers with Windows.  It looks like the error you posted is that the mount of the ext4 partition 2 failed because at the same time, there was a filesystem being built on it.  Did you hashcheck the downloaded ISO?
  See [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
  Check the number against the listing in the link for your release listed at
  [http://releases.ubuntu.com](http://releases.ubuntu.com) under the MD5SUMS link.
  For other releases' hashes, like lubuntu, see:
  [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

---

### Post by ajgreeny on 2017-04-12
Try leaving the whole disk unallocated and then choose to install using "Something Else" to the whole disk without making partitions manually.
Make sure you ask the installer to install grub into the root of the 32GB USB disk as you show in your second image, ie /dev/sdc

---

### Post by C.S.Cameron on 2017-04-12
First unplug your hard drive, and then you won't need to use "Something else" for a typical install.

If you want a NTFS partition on the Full install USB for Windows data, format the drive NTFS before proceeding then use "Something else" to build your partitions, leave the first partition NTFS.

---

### Post by kurt18947 on 2017-04-12
> **C.S.Cameron said:**
> First unplug your hard drive, and then you won't need to use "Something else" for a typical install.

If you want a NTFS partition on the Full install USB for Windows data, format the drive NTFS before proceeding then use "Something else" to build your partitions, leave the first partition NTFS.

Unplugging the hard drive is an excellent suggestion. I have a somewhat buggered up GRUB right now because I didn't. I'm pretty sure I did the "something else" then asked the installer to place GRUB on the USB drive. It didn't. The second time I bought a screwdriver (I was away from home), removed the hard drive and plugged in both live USB and 32 GB flash drive target. It worked fine. I didn't create a swap partition on the flash drive, I've read it's not necessary and I believe the newest Ubuntu installers create a swap *file* instead which is what I've done in the past. I couldn't use hibernation but I never have and have read it doesn't work well on *buntu anyway.

---

### Post by ajgreeny on 2017-04-13
UEFI makes the placement of grub so much more difficult than it is with BIOS/MBR; wherever you ask the Ubuntu installer to put grub, UEFI insists that it is put in /dev/sda.

For that reason disconnection of the first hard disk is a good idea to avoid all possibilities of messing up an existing bootloader system.

---

