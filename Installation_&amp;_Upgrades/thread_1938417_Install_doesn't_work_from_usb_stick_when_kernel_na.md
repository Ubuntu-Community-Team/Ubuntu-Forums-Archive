---
title: "Install doesn't work from usb stick when kernel names it /dev/sda"
date: 2012-03-09
forum: Installation &amp; Upgrades
---

### Post by j8kel on 2012-03-09
I am trying to do a silent install of Ubuntu 10.04 lts server from a usb drive.  It works fine for some machines, but whenever I use it in a machine where the usb stick gets mounted as /dev/sda instead of /dev/sdb, the machine won't boot from its hard drive after the install.

I have tried using udev in the initrd of the usb drive to make sure the usb drive is renamed to /dev/sdb, but /proc/partitions doesn't get updated, and even though the install finishes without errors, the machine can't be booted.  It just shows a black screen with a blinking cursor in the corner.  If I reinsert the usb drive while it is in that state, the machine will boot properly from the hard drive.  So I know the files were copied successfully.

The udev rules I'm using are here, I put them in /etc/udev/rules.d/99-my.rules
```
NAME="sdb%n",KERNEL=="sda*",ENV{ID_BUS}=="usb",RUN+="/usr/bin/logger 'DEBUG:::1 kernel matched sda* renaming to sdbn [%E{ID_BUS}][%E{ID_FS_UUID}][%k][%E{ID_FS_LABEL_ENC}]"
NAME="sda%n",KERNEL=="sdb*",ENV{ID_BUS}!="usb",RUN+="/usr/bin/logger 'DEBUG:::2 kernel matched sdb* renaming to sdan [%E{ID_BUS}][%E{ID_FS_UUID}][%k][%E{ID_FS_LABEL_ENC}]"
```I have tried renaming the rules so they are run at different times.  I tried 61-my.rules, 59-my.rules, and 00-my.rules.  Each time, I confirm that the debug messages appear in the syslog.

If I stop the installer at the configure keyboard prompt and do an ls /dev/sd*, I see
/dev/sdb    /dev/sdb1    (no /dev/sda) as I expect, but if I cat /proc/partitions, I still see
/dev/sda  and  /dev/sda1  (no /dev/sdb)

At the end of the installer, checking ls /dev/sd*, I see the usb drive partition named sdb* and the hard drive partitions named sda*, but /proc/partitions still shows the usb drive as sda, and the hard drive as sdb.

I can see during the install that the following grub commands are run:
```
grub-install /dev/sda
grub-update
```

As a control test, I built a usb drive using Pendrivelinux's Universal USB Installer and used it to install Ubuntu 10.04 lts desktop.  It also mounted the usb drive as /dev/sda, and completed successfully, but the machine failed to boot.  I know it is not a bad machine because I have tried it on 3 dells of the same model, all with the same issue.


Any help or ideas would be greatly appreciated.

---

### Post by oldfred on 2012-03-09
Grub's default install of the boot loader is to sda. Not sure how to change that for devices that promote an external device to sda other than using manual install.
You should be able to fix it with a grub install to the internal drive. Grub also remembers which drive to use for reinstalls, so you also may have to update that.

If you can boot:
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc
#to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

Or fix boot loader then run the commands above.
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

Supergrub may let you boot and then you can repair grub from your install.
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

---

### Post by ScientificProp on 2012-03-09
I'm not experienced enough with Ubuntu to follow much of the details in your post, but I can share my recent experience trying to boot a USB HDD with Ubuntu 11.10 64 bit. Basically, I was never able to successfully boot Ubuntu from a USB HDD when I installed from a LiveUSB. But, if I installed from a LiveCD, then I was able to boot Ubuntu from the USB HDD. I installed and started running 11.10 64 bit yesterday, so as I said I'm learning Ubuntu and Linux.
Apparently, this goes against common expectations, but I repeated this many times and am confident in this result.

ScientificProp.

---

