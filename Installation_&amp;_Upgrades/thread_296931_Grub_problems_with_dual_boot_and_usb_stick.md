---
title: "Grub problems with dual boot and usb stick"
date: 2006-11-10
forum: Installation &amp; Upgrades
---

### Post by cooleric1234 on 2006-11-10
I just tried to install 6.10 in a dual boot configuration. I used the alternate CD and tried to install GRUB to the partition, instead of the MBR. Then I altered the windows boot loader to accept the first 512 bytes of the necessary partition. It seems to work, as in GRUB is loaded, but it says something about a partition not found or something. I know what the problem is though.

When I did the install I had a usb thumb drive in my system. It showed up as /dev/sda in Ubuntu and the hard drive was /dev/sdb. So GRUB used /dev/sdb for all of it's references. But now that I reboot and use the windows bootloader it looks like the drives are switched, the usb is /dev/sdb and the hard drive is /dev/sda. I tried the rescue mode and changing devices.map, but I don't know what I'm doing. I guess I have to re-run grub after making that change? Plus, there are lines in menu.lst that point straight to /dev/sdb (like where the kernel is). I've never used GRUB, but it seems so much more complicated than LILO. Anybody know how to change these settings and re-install grub to the partition, not the MBR?

---

### Post by bulldog on 2006-11-10
Try first ```
sudo update-grub
```
If that's not going to do it,you can alter your menu.lst manually and change the  entry's to your needs.
To enter your menu.lst```
gksudo gedit /boot/grub/menu.lst
```

---

