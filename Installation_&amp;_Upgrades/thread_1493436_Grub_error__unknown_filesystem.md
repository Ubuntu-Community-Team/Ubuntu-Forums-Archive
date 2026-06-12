---
title: "Grub error : unknown filesystem"
date: 2010-05-25
forum: Installation &amp; Upgrades
---

### Post by sooperspook on 2010-05-25
I have an ASUS EEE 901 which i had previously installed Ubuntu on. I tried to upgrade recently to 10.04  using a flash drive, since I don't have a cd drive on it.
Now every time I try to boot I get

error:unknown filesystem
grub rescue>

I tried looking up grub rescue commands but I can't make heads nor tails of it.

Looking through solutions posted here for other people who've had similar problems it seems they all require me to boot with a LiveCD, which I obviously can't do.

any ideas?

---

### Post by oldfred on 2010-05-25
Often all you have to do is reinstall grub.

Your USB that you used for installing should be the same as a liveCD except bootable from a USB port.

---

### Post by sooperspook on 2010-05-26
I tried that but I get the same error message even when i boot from the usb drive.

---

### Post by oldfred on 2010-05-26
If you are getting the same message, are you sure you switched to boot from the USB. If you were able to install from it you have to be able to boot and then the error message must be from your internal drive.

---

### Post by bcbc on 2010-05-27
From the grub rescue, you should be able to boot your ubuntu installation using the following commands. If you know what partition ubuntu is on, then don't bother with the ls commands. e.g. /dev/sda1 is (hd0,1) and /dev/sda5 is (hd0,5), /dev/sdb1 is (hd1,1) etc.

```
#show you the available partitions
ls
#look for boot files on the partitions
ls (hd0,1)/boot
# continue until you see vmlinuz-2.6.xxxx
#then boot that linux replacing hd0,1 with your partition
insmod ext2
set root=(hd0,1)
# in the next command sda1 represents (hd0,1), sdb2 would be for (hd1,2)
linux /vmlinuz root=/dev/sda1 ro quiet splash
initrd /initrd.img
boot

```

Then once you've booted successfully, you just install the grub bootloader and regenerate your grub menu for good measure:
```
sudo grub-install /dev/sda
#and just in case
sudo update-grub
```

And you should be good to reboot.

Caveat: I just tried the above instructions and it booted my ubuntu - with the following difference. Since I booted from my usb, grub sees it as (hd0) but it's /dev/sdb. If you boot from your harddrive, then the mapping shown above (hd0 = sda) should work.

---

