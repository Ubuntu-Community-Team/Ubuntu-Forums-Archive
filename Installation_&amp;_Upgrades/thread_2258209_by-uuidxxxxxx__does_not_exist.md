---
title: "/by-uuid/xxxxxx  does not exist"
date: 2014-12-25
forum: Installation &amp; Upgrades
---

### Post by Duckmanjbr on 2014-12-25
I have a brand new Acer Aspire E11 and have installed Ubuntu on it.  It installs fine and runs w/ no issue until I reboot.  On reboot it seems like the drive isn't found.  I've come to this by looking into /dev/disk/by-uuid/ and the only partition there is the swap partition.  I have tried to extend the boot time by adding a rootdelay=3 into my /boot/grub.cfg however this had no effect.  To make this problem even more odd is that if I run a boot-repair from a liveUSB it will work for 2-3 reboots and then stop working again.  Does anyone have any idea as to what could be going on?

boot-repair log:[URL="http://paste.ubuntu.com/9619788/"]
http://paste.ubuntu.com/9619788/[/URL]

---

### Post by yancek on 2014-12-25
Your boot repair output shows an ext4 partition on your drive.  Is this an SD card?  The output below shows the partitions on the drive/SD Card.  The first one would be the system partition with Ubuntu and the second obviously the swap.  There is nothing showing Grub on the drive only on your 8GB flash drive.

> /dev/mmcblk0p1: UUID="fe472e38-fa80-4fb2-b5ec-2c69dccdec44" TYPE="ext4"
/dev/mmcblk0p5: UUID="c54027d0-7086-4168-b98a-d21f77c46bec" TYPE="swap"

I've never used an SD card so don't know what the differences would be.  After you run boot repair, are you removing the flash drive and changing boot priority to the internal drive?  You might get some ideas from the link below:

[http://unix.stackexchange.com/questions/118090/mounting-mmcblk0p1-failed-with-invalid-argument](http://unix.stackexchange.com/questions/118090/mounting-mmcblk0p1-failed-with-invalid-argument)

---

### Post by MAFoElffen on 2014-12-25
'mmcblk*xxx*' is usually media storage notation for Android devices... then the SD card reference. What is this device? It says there is no grub installed to the device media. Following the logic of what is there and what is recommended at the end should fix it. (installing grub to the media with the /boot directory in partition one of that media and the boot mbr installed in the root of that media...)

---

