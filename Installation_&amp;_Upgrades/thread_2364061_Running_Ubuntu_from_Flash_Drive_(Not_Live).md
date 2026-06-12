---
title: "Running Ubuntu from Flash Drive (Not Live)"
date: 2017-06-18
forum: Installation &amp; Upgrades
---

### Post by mn_voyageur on 2017-06-18
I would like the ability to load Ubuntu to a flash drive.

This will allow me to run on any computer with having to deal with Windows.

I created a Live version, but rebooting erased my desktop modifications.

Is there a method to install Ubuntu on a flash drive?  I have a 64GB flash drive that I was going to use.

Thanks,
MarkN

---

### Post by RobGoss on 2017-06-18
Hello and welcome to the forum, Yes there is a method to install Ubuntu on a USB stick this post should help you with questions you might have see this post [https://askubuntu.com/questions/397481/how-to-make-a-persistent-live-ubuntu-usb-with-more-than-4gb](https://askubuntu.com/questions/397481/how-to-make-a-persistent-live-ubuntu-usb-with-more-than-4gb)

---

### Post by yancek on 2017-06-18
Doing a full install of Ubuntu to your 64GB flash drive works the same as installing to an internal or external hard drive.  You need to select the proper drive to install to.  Are you familiar with Linux naming conventions for hard drives and partitions?  If you have Ubuntu on a DVD or flash drive, boot it with your 64GB plugged in and post the output of either sudo fdisk -l or sudo parted -l and someone should be able to point you in the right direction.  You could also do a persistent install explained in the link posted above.

---

### Post by Dennis N on 2017-06-18
Be sure to use a USB 3.0 flash drive booting from a USB 3 port. Otherwise, performance will be painfully slow.

---

### Post by oldfred on 2017-06-18
And is system UEFI or BIOS?
I prefer to use gpt partitioning for all drives. The only place you cannot use gpt is if booting Windows in BIOS mode as it requires MBR(msdos). But you cannot boot Windows from external drive anyway.

If UEFI you should use gpt and must have an ESP - efi system partition on external drive. The ESP is a FAT32 formatted partition with the boot flag if using gparted. Normally first partition.

But grub only installs to ESP on sda and /EFI/ubuntu. And UEFI only boots external drives from ESP on external drive and /EFI/Boot/bootx64.efi, so some manual copying& renaming of files is required.

        [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

My 64GB drive:
```
Disk /dev/sdc: 61.9GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name       Flags
 1      1049kB  211MB   210MB   fat32        ESP        boot, esp
 2      211MB   213MB   2097kB               bios_grub
 3      213MB   22.9GB  22.6GB  ext4         system
 4      22.9GB  61.9GB  39.1GB  ext4         data

```

And full install with no updates (yet) and no log files & other apps that start to fill / (root).
```
/dev/sdc3        21G  4.0G   16G  21% /media/fred/system
/dev/sdc4        36G   16G   19G  46% /media/fred/data

```

---

### Post by him610 on 2017-06-18
Hello mn_voyager,

Here is the link to a tutorial that uses the *mkusb* tool which you can download and use to create your live usb stick The author of both the tutorial and *mkusb* is sudodus, staff emeritus, of the Ubuntu Forums.
[https://ubuntuforums.org/showthread.php?t=1958073](https://ubuntuforums.org/showthread.php?t=1958073)

This is the only utility I use to create live distros on usb, and the documentation of the process is excellent.

---

### Post by monkeybrain20122 on 2017-06-18
You can do that, but it will be slow. Performance would be much better if you install in an external hd instead, procedure is the same and apart from boot time it is like installing internally even with only a usb2 port. I have done this many times.

---

