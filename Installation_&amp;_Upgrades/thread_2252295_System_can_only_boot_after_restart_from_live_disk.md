---
title: "System can only boot after restart from live disk"
date: 2014-11-10
forum: Installation &amp; Upgrades
---

### Post by daniel212 on 2014-11-10
I first installed Ubuntu 12.04 LTS in 2012 on two identical machines. After completing the installation, I rebooted the computers and everything seemed to be fine; however, after the computers were shutdown entirely and then turned on again, each displayed the BOOT DISK ERROR message. 

I tried reinstalling Ubuntu only to encounter the same problem. Eventually I figured out that by booting into the live disk first and restarting, I could access the system. This behavior is similar to that described in this post: [http://ubuntuforums.org/showthread.php?t=1389025](http://ubuntuforums.org/showthread.php?t=1389025), however, I only have a single hard disk system, so the solution they found would not work for me. I have reinstalled grub using boot-repair, but it still doesn't work. 

Basically, for the past two years I have been using this system like normal, and have updated to 13.04 and now 14.04, yet whenever I want to start the system up, I have to use the live disk. Does anyone know of a way of fixing this problem? The boot info summary for my computer can be found at [http://paste.ubuntu.com/8930298/](http://paste.ubuntu.com/8930298/).

---

### Post by yancek on 2014-11-10
What is the 2GB unpartitioned FAT32 flash drive used for?  Do you have the 500GB drive, the drive with Ubuntu, set to first boot priority in the BIOS?

---

### Post by daniel212 on 2014-11-10
That was a flash drive plugged in at the time, and yes, I have configured the boot order in every way I can to no avail. The bizzare thing is that this behavior occurs in exactly the same manner on both machines.

---

### Post by daniel212 on 2014-11-16
After a bit more digging I'm getting closer to figuring out the cause of the problem, though I'm not much closer to solving it. I tried to install grub on to a flash drive with the boot directory pointing to the hard drive, and the installation onto the usb worked fine, but when I tried to boot from it it gave me an "error: no such device: [uuid]". By doing ls from grub rescue i discovered that the hard drive wasn't being detected, only the flash drive. Oddly enough, when I attempted to install extlinux, an alternative to grub, I started getting a different error, something like missing operating system, when attempting to boot from the hard drive.

---

### Post by daniel212 on 2014-11-16
The hard drive is still being detected be the bios though, just not grub. Also, I forgot to mention that I *did* attempt to switch around the boot order of the hard drives to see if that would change anything and it didn't help.

---

### Post by krupier on 2014-11-16
> **daniel212 said:**
> Oddly enough, when I attempted to install extlinux, an alternative to grub, I started getting a different error, something like missing operating system, when attempting to boot from the hard drive.
Nothing odd to me here. Different bootloader, different output. Seems like you haven't installed GRUB correctly. What message do you get while installing GRUB? Did you installed it on /dev/sdb? Your setup is a bit strange to me. My harddrive is always being shown as **sda**, regardless of what media I start my system from. However for you it is sdb. Can you show us how you install your bootloader, please?

---

### Post by daniel212 on 2014-11-16
The error I get when using the grub bootloader is from the motherboard, something I confirmed by disconecting the hard drive entirely. What was weird was that when using extlinux, I no longer got an error from the motherboard, but the bootloader itself.  So I don't think the problem is an incorrect installation of grub. In fact, grub loads entirely off of the hard drive perfectly fine after restarting from a live disk, which makes me think it's not the problem. As far as I can tell, the issue is that the motherboard does detect the hard drive, but not correctly.

I recently found in the bios that the sata type was set to native ide mode rather than ahci, so I changed it hoping that it would fix my problems. Unfortunately, it idn't, but it did present a different screen when booting that shows the status of the hard drives. Normally, it prints hdd / smart error. Then, after rebooting from a live disk, it prints ok instead.

Additionally, I have pluged in a blank hdd and found that it prints ok all of the time, so it appears to be some problem with drive detection.

---

### Post by leclerc65 on 2014-11-16
I remove all SD cards from my computers, except my Asus eeePC. The problems are not worth leaving them permanently inside.

---

