---
title: "problems installing from usb flash drive"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by obijywk on 2007-04-23
I'm trying to follow the instructions from [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

I think it's really close to working. My computer successfully boots off the USB flash drive and starts the Ubuntu installer, which can't find the installation cd-rom as expected. As outlined in the instructions from the wiki, after that happens I switch to a console and try to mount the flash drive at /cdrom.

When I try to mount the flash drive with "mount -t vfat /dev/sda1 /cdrom" I get the mount error "No such device". I've checked and "/dev/sda1" and "/cdrom" are both definitely there. I've also looked at the boot messages in dmesg and the kernel definitely finds sda (my kingston USB flash drive) and sda1.

One idea I had is that the 'vfat' driver is not available. Is it possible that vfat is not included on the alternative installation boot cd? When I look at lsmod I see that 'ext2' and 'isofs' are there, but not 'vfat'. Also, 'modprobe vfat' fails. If vfat really is missing, is there some way I can easily add a vfat module to my flash drive?

I initially copied the contents of "ubuntu-7.04-alternate-i386.iso" to the flash drive, so you know what I'm working from.

Thanks!

---

### Post by obijywk on 2007-04-24
Well, I didn't exactly fix the problem, but I got the 7.04 desktop live CD "ubuntu-7.04-desktop-i386.iso" to run off of my flash drive. I followed the instructions from the wiki page [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick) for the most part, then when I actually booted the machine I typed "live root=/dev/sda1" to instruct it that the cdrom files were actually on the flash drive. This booted (eventually, the flash drive is pretty slow) into the 7.04 liveCD from which I could install Ubuntu. It's slowly installing right now but it seems like it is going to work.

EDIT: There's one more change I had to make - after the system installed, the 'root=/dev/sda1' parameter I used initially was added to the default grub configuration, so I had to remove it from grub for the system to start properly.

---

