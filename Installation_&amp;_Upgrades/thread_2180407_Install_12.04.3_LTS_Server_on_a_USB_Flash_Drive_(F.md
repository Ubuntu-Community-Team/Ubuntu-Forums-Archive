---
title: "Install 12.04.3 LTS Server on a USB Flash Drive (Full time on USB)"
date: 2013-10-12
forum: Installation &amp; Upgrades
---

### Post by Casey_Friday on 2013-10-12
I've just put together my first NAS, and I'm quite excited about getting it up and running!  Here are the parts I'm using, for reference.

**Case**: Fractal Node 304
**Motherboard**: ECS H61H2-I3
**Processor**: Intel Celeron G1610 (2.6GHz Ivy Bridge)
**RAM**: 8GB DDR3 ADATA (2 x 4GB)
**HDD**: 4 x WD Red 2TB Drives (Planning to run all four drives in RAID5)
**PSU**: HEC 350TA-2RK

I've put everything together, but I really want to use 100% of the WD Red drives for storage, so I want to run the OS completely on a USB drive.  I've tried multiple ways of doing this.  The problem is, I'm trying to run Ubuntu Server (no need for GUI), and it appears the server version of Ubuntu doesn't have a "Try it" feature, only an "Install it" feature.

_**The Problem**_

I first created an install CD on my USB drive, but when I plugged that into my NAS, hoping to just install completely to the USB; however, the install medium would only let me install to any drives OTHER than the actual USB install medium.  That turned out to be a no go.

I then went for a second attempt.  I burned a 12.04.3 Server DVD, booted my laptop to that DVD, and attempted to install to the USB from there.  All seemed to go well, but when I tried to boot from the USB at that point, I saw GRUB, selected the Server OS, then I got a black screen with a blinking cursor in the upper left hand corner.  I let it run for about 5 minutes, and no change.  It just wouldn't boot.

My third attempt is what I've just done - I installed 12.04 x64 Desktop on my laptop.  I then downloaded the x64 Server 12.04 image and used StartUp Disk Creator to make a startup disk.  I chose to use 4GB of persistence.  **Is the simple act of ticking the persistence box going to make this an active install, rather than just an installer USB?**

I attempted to boot from my newly created USB, and I got the Ubu Server setup screen, so it seemed to go well, but I figured I should wait to actually run the install until I plug it into my NAS.  Will it allow me to keep the install on the USB, or do I need to get a second USB drive to accomplish this USB-only setup I'm trying to achieve?

Thanks in advance!

---

### Post by ubfan1 on 2013-10-13
No, selecting persistence does not make a full install.  It allows you to save your files, and even install/update packages, but some things just cannot
be done with just persistence.  Things like updating the kernel, and even chaning the /etc/fstab file I recall, cannot be done.  There is lots of good advice on this topic here and in [http://askubuntu.com/](http://askubuntu.com/).  
  You can have a USB live (install) media, and use it to install to another USB.  There are some things to tweak for performance like aligning the partitions/filesystem to the erase block size (or just use a 4M alignment since there is no easy way I know of to get the usb erase block size (as opposed to the simple way to get that for SD cards).  Move as much as possible into ram, like /tmp ...  All just tweaking for perf.  You might bump in an old bug on the usb to usb install bug #384633), and have to edit the first grub.cfg to fix any wrong devices, but after first boot, run sudo update-grub to fix things.

---

### Post by Casey_Friday on 2013-10-13
I couldn't get it to install from a portable hard drive, but I finally found another USB Flash drive in the house, so I was able to install from Flash Drive to Flash Drive.

Now to get my RAID5 setup handled!

---

