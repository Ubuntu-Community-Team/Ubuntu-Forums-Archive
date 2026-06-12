---
title: "installing on Macbook Pro without OSX or CD drive"
date: 2013-01-04
forum: Installation &amp; Upgrades
---

### Post by jdc on 2013-01-04
There are a lot of posts about installing Ubuntu on a Mac, but most assume you have a working OSX installation or a working CD drive.  My Mac hasn't been able to boot from CD/DVD for some time, and I've got a blank hard drive that I'd like to install Ubuntu 12.04 on.

I've read lots of posts about using a USB drive to boot, but most are followed by people saying the method didn't work for them, or they require you to install refit, which I don't think I can do since I don't have OSX.

I could also hook the empty hard drive to another machine running Ubuntu and prepare a partition on it to do the install from.  

Any advice about which route to take?  Which ISO to use (32/64 bit, Mac version, etc)?  How to prepare the USB drive/hard drive?

My machine is a 15-inch MacBook Pro 1440x900 Santa Rosa from mid 2007, MacBookPro3,1.

Thanks for any help!

---

### Post by Rocklobster690 on 2013-01-04
Check out Single-Boot: Ubuntu Only - [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

Good Luck!

---

### Post by Rocklobster690 on 2013-01-04
> **jdc said:**
> There are a lot of posts about installing Ubuntu on a Mac, but most assume you have a working OSX installation or a working CD drive.  My Mac hasn't been able to boot from CD/DVD for some time, and I've got a blank hard drive that I'd like to install Ubuntu 12.04 on.

I've read lots of posts about using a USB drive to boot, but most are followed by people saying the method didn't work for them, or they require you to install refit, which I don't think I can do since I don't have OSX.

I could also hook the empty hard drive to another machine running Ubuntu and prepare a partition on it to do the install from.  

Any advice about which route to take?  Which ISO to use (32/64 bit, Mac version, etc)?  How to prepare the USB drive/hard drive?

My machine is a 15-inch MacBook Pro 1440x900 Santa Rosa from mid 2007, MacBookPro3,1.

Thanks for any help!

Check out Single-Boot: Ubuntu Only - [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

Good Luck!

---

### Post by 2F4U on 2013-01-05
> I could also hook the empty hard drive to another machine running Ubuntu and prepare a partition on it to do the install from.

If you have a machine that already runs Ubuntu, you can use Startup Disk Creator to put the installation image on a usb stick.

CD images to be used by Mac users can be found here:

[http://releases.ubuntu.com/12.04/](http://releases.ubuntu.com/12.04/)
[http://releases.ubuntu.com/12.04.1/](http://releases.ubuntu.com/12.04.1/)
[http://releases.ubuntu.com/12.10/](http://releases.ubuntu.com/12.10/)

As far as I know, you can go 64 bit with that machine.

---

### Post by jdc on 2013-01-05
The replies posted so far require booting from CD or USB, both of which I can't do.

I did however find this page [https://help.ubuntu.com/community/Installation/FromLinux]("https://help.ubuntu.com/community/Installation/FromLinux") which explains how to install Ubuntu from an iso that has been unpacked onto a hard drive partition.  And this worked for me.  I partitioned the drive ahead of time so that it wouldn't need to be repartitioned while the installer was running from it, and I needed to delete the cdrom line from /etc/mtab as mentioned at that link.

---

