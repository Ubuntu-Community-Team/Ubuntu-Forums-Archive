---
title: "Persistence size USB-drive (Live USB-stick)"
date: 2014-12-08
forum: Installation &amp; Upgrades
---

### Post by Some101 on 2014-12-08
Hello,

I would like to create a live USB-drive with Ubunutu on it. However, I read that it is possible to extend the persistence size over a 4 GB. I have followed different tutorials but when I boot my drive again with the 'extended' partition I get a blinking cursor at my POST and it wont boot. I used several USB-drives. 
The tutorials I followed were:
[http://askubuntu.com/questions/397481/how-to-make-a-persistent-live-ubuntu-usb-with-more-than-4gb](http://askubuntu.com/questions/397481/how-to-make-a-persistent-live-ubuntu-usb-with-more-than-4gb)
[http://www.pendrivelinux.com/create-a-larger-than-4gb-casper-partition/](http://www.pendrivelinux.com/create-a-larger-than-4gb-casper-partition/)

Thanks.

---

### Post by ubfan1 on 2014-12-08
Well the 39748 answer looks pretty complete.  How are you creating the USB?  If you put a 4G FAT partition on your (larger) usb, and make the rest an big ext2 partition. You may create a normal presistence file of 1G minimum, then when it works,  label the big ext partition "casper-rw"  and just rename the caster-rw file on the FAT partition to something like old-casper.  That may be enough to boot, or if not, try mounting the old-casper file as a loopback, and copy whatever's there to the partition.  Anyway, you can always go back to the casper-rw file by renaming it and relabeling the partition

---

### Post by nerdtron on 2014-12-08
If you like a persistence higher than 4GB (because of the 4GB file limit of FAT32) why not try doing a full install to the USB.
If your drive is 16GB, you'll still have plenty of space.

---

### Post by C.S.Cameron on 2014-12-09
Following step by step works for me when making a persistent flash drive:

Boot Live CD or Live USB.
Plug in flash drive.
Start gparted.

Create 2 GB FAT32 partition, (on the left side of the bar). (size is optional, extra space can be used for file storage and transfer to Windows machines).

Create a 4 GB ext2 partition to the right of this, labeled it "casper-rw". (ext3 and ext4 also work).

Create a partition in the remaining space and label it "home-rw". (optional, creates a separate home partition).

Close gparted.
Un-mount and re-mount flash drive.
Start "Create a live usb startup disk", (usb-creator).
Select "Discard on shutdown".
Press "Make Startup Disk.
When usb-creator finishes, Go to the root folder of your Live USB
    Enter the syslinux directory, (or for UNetbootin the root directory).
    Make the syslinux.cfg file writeable
    Replace the contents of the file syslinux.cfg with:

```
    default persistent
    label persistent
      say Booting a persistent Ubuntu session...
      kernel /casper/vmlinuz
      append  file=/cdrom/preseed/ubuntu.seed boot=casper persistent initrd=/casper/initrd.lz quiet splash noprompt --
```

Shutdown, remove CD, reboot.


First time booting go to users and groups and create an account with yourself up as an Administrator, with password if desired.

Note:
The above code will bypass the Try/Install and Language screens.
Code is for 32bit versions, if using 64 bit change vmlinuz to vmlinuz.efi.

---

### Post by Some101 on 2014-12-09
Thanks everyone for your reply. I did a full install on de USB-drive like Nerdtron suggested. However, I still see the Windows 7 loader in the Ubuntu Boot Menu (similar to the picture below):[IMG]http://www.techotopia.com/images/3/37/Ubuntu_11_dual_boot_menu.jpg[/IMG]

Is there a way to get rid of it so that so it automatically starts Ubuntu after I selected my USB-drive?

---

### Post by nerdtron on 2014-12-09
> **Some101 said:**
> Thanks everyone for your reply. I did a full install on de USB-drive like Nerdtron suggested. However, I still see the Windows 7 loader in the Ubuntu Boot Menu (similar to the picture below):[IMG]http://www.techotopia.com/images/3/37/Ubuntu_11_dual_boot_menu.jpg[/IMG]

Is there a way to get rid of it so that so it automatically starts Ubuntu after I selected my USB-drive?

You did a full install on the USB without removing the internal drives first? I do hope you installed the Linux bootloader, GRUB, on the USB and not on the windows drive.

To remove any windows 7 entries, disconnect any windows drive, Boot into the Mint installed on the USB, open a terminal and run "sudo update-grub".
This will scan all drives and operating systems. Since it windows is already disconnected, and Mint won't find it, the windows entries will be deleted.

---

### Post by C.S.Cameron on 2014-12-10
If you disable the hard drive Windows is installed on, boot the USB and run update-grub, it will remove Windows from grub.
Plug the internal drive back in.
Now the grub menu should not appear at boot unless you press the shift key.
However you will not be able to boot Windows when booting from the flash drive.

---

