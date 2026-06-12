---
title: "Installing 10.04 Netbook Edition on EEE PC 701"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by yaqwsx on 2010-05-02
Hi,

I'm currently trying to install 10.04 Netbook Edition on my EEE PC 701, but the installation process stops with the following message:

```
(initramfs) /init: line 7: can't open udevadm settle - timeout of 180 seconds reached, the event queue contains: /sys/devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.0/host3/target3:0:0/3:0:0:0/block/sdc/sdc1 (1098) /dev/loop0: no such file

mount: mounting udevadm settle - timeout of 180 seconds reached, the event queue contains: /sys/devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.0/host3/target3:0:0/3:0:0:0/block/sdc/sdc1 (1098) /dev/loop0 on //filesystem.squashfs failed: No such device

Can not mount udevadm settle - timeout of 180 seconds reached, the event queue contains: /sys/devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.0/host3/target3:0:0/3:0:0:0/block/sdc/sdc1 (1098) /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs
```9.10 NBR was running perfectly fine, so I don't know what to make of this. Any ideas?

Thanks in advance!

---

### Post by hottyson on 2010-05-12
> **yaqwsx said:**
> Any ideas?

I just installed 10.04 netbook on my eeepc 701. I had no problems other than a very slow boot up of the live-cd.

Perhaps your cd has errors?
Or, perhaps your cdrom drive is not playing nice with the eeepc 701?

Maybe try reburning with slower burn speed, or try a different cdrom drive?

---

### Post by vyvee on 2010-05-13
I've just [installed 10.04 UNE on my Eee PC 701]("http://www.vyvy.org/main/en/node/211") too, and it works just perfectly out-of-box.

I will suggest that you try the following:
* Make sure that the image you've downloaded is really ok. (correct MD5SUM)
* Reset the BIOS setting to the default and try again.
* Have you modified the hardware of your Eee PC before? Probably some device problem.

[This link]("https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Asus%20Eee%20701-SD%20/%20702") may be helpful but none of the bugs shown seems to describe the problem you face.

---

### Post by vyvee on 2010-05-13
hottyson, just wonder if you use an external CD-ROM to boot the Live-CD? I install it using a USB stick, as Eee PC 701 supports booting from USB. I think using USB stick is 'safer' as you don't need to worry about the burn speed, quality of the CD, etc.

---

### Post by yaqwsx on 2010-05-13
Maybe it is indeed a device problem. As I said, 9.10 NBR is running fine, but neither 10.4 nor the latest version of EasyPeasy works. I always get the same error message. I didn't modify the hardware. And yes, I use a USB stick.

I think I should run some memory tests...

Thanks anyway.

---

### Post by thebrother23 on 2010-05-26
Has anyone else had a problem with the Ubuntu Netbook Edition 10.04 install on a 701 4Gb? 
I tried it from a USB key last night and was delighted with it, so I decided to install it permanently. After it formatted the disk and got to about 50% install, it suddenly announced it was out of disk space. I gave up and went to bed.
This morning, it won't even boot from the USB. Now I get the initial boot screen followed by a flashing cursor, and that's it. Very disappointing.
Shift+F10 allows me access the Atheos Boot Agent config menu. I also have access to the BIOS setup. I've tried various boot options without any success. Just that annoying flashing cursor.
Has anyone else managed to get out of this mess?
PS I guess the F9 factory settings restore was wiped as part of the reformat...

---

### Post by thebrother23 on 2010-05-26
> **thebrother23 said:**
> Has anyone else had a problem with the Ubuntu Netbook Edition 10.04 install on a 701 4Gb? 
I tried it from a USB key last night and was delighted with it, so I decided to install it permanently. After it formatted the disk and got to about 50% install, it suddenly announced it was out of disk space. I gave up and went to bed.
This morning, it won't even boot from the USB. Now I get the initial boot screen followed by a flashing cursor, and that's it. Very disappointing.
Shift+F10 allows me access the Atheos Boot Agent config menu. I also have access to the BIOS setup. I've tried various boot options without any success. Just that annoying flashing cursor.
Has anyone else managed to get out of this mess?
PS I guess the F9 factory settings restore was wiped as part of the reformat...

Finally got sorted. Reformatted the USB key and restarted the Startup Disk process from scratch. More importantly, in the BIOS settings, I changed the "boot first from" option to the USB drive instead of the default (now corrupted) internal hard drive. To do this, start the PC, and then start hammering on Shift+F2 until the BIOS settings pop up. You'll find the boot order menu in there.
Reinstalled Ubuntu Netbook Edition from scratch, and all is well! Happy days.

---

