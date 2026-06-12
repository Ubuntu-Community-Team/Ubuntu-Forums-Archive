---
title: "ext2 install on acer aspire one"
date: 2008-11-19
forum: Installation &amp; Upgrades
---

### Post by kitchensink on 2008-11-19
Hi,
   I just purchased a acer aspire one with 16GB SSD.  I am in the install process of xubuntu on the acer.  I have set the display size and got to font to work correctly.  I want to install the OS with ext2.  The default is ext3.  Can I change to ext2 after installing the OS with ext3 to ext2.  Is there any way to install with ext2.  Please help

Thanks

---

### Post by psusi on 2008-11-19
```
sudo tune2fs -O ^has_journal /dev/sda1
```

Or whatever the partition in question is.  It must not be mounted at the time, so you need to run it from the livecd or something if you are doing this to your root partition.

---

### Post by kitchensink on 2008-11-19
Ok, I finally installed xubuntu 8.10 on the harddrive as ext2.  I now have an error saying "Error 15"  when I boot up without the USB.   Please please help.  is it a grub issue or a fstab change.  Please help..

Thanks

---

### Post by psusi on 2008-11-19
What do you mean "without the usb"?  If you had a different drive plugged in when you installed and then removed it, it could have changed the identifier of the other drive, so you will need to reinstall grub.

---

