---
title: "only grub rescue after installing 18.04 in mini-pc"
date: 2018-10-17
forum: Installation &amp; Upgrades
---

### Post by Marko_Niinimaki on 2018-10-17
The PC: [https://liliputing.com/2015/06/egreat-i6-mini-pc-review.html](https://liliputing.com/2015/06/egreat-i6-mini-pc-review.html) Safe boot turned OFF. OS: Win10 32bit home edition. The internal SSD is only 32 GB so I'm trying to install Ubuntu on an SD that is in the PC's slot.

The PC uses some EFI tricks. For instance in order to make it boot from a USB drive, I need to copy "bootia32.efi" file into the drive's \efi\boot directory.
I can start the installation of 18.04 from a USB with that. Installation steps: "Install Ubuntu alongside Windows boot manager", select media -> the SD in the slot (not internal), format partitions to ext4. The installation finishes without errors.

After I reboot and remove the USB, BIOS shows 3 boot options: ubuntu, windows boot manager, EFI shell. Windows boot manager and EFI shell were there before. Select ubuntu -> disk "long id" not found -> grub rescue. Shows (hd0), (hd0,msdos1), (hd0,msdos2), (hd1), (hd2). If I do "ls (hd0)/" or any other ls, grub responds: Unknown filesystem. Booting into Windows works but no "ubuntu" selection visible anywhere.

---

### Post by QIII on 2018-10-18
Hello!

Please use the default font and color unless you wish to draw attention to a specific part of your post.

Thanks.

---

