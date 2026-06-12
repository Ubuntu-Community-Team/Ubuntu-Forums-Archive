---
title: "Installing Ubuntu without a CD Drive"
date: 2008-07-29
forum: Installation &amp; Upgrades
---

### Post by jgirata on 2008-07-29
Hi,

I'm trying to install Hardy Heron on a VIA Pico-ITX Builder Kit (a 1 GHz processor, 1 GB RAM mini-computer).  The kit, however, does not have have a CD drive; it only has 4 USB ports.  Also, there is no pre-installed OS to boot into to download any software.  I'm hoping that there is just some way to copy the contents of the Live CD onto an external hard drive and boot from that, but I haven't been able to figure it out.

Thanks in advance for any help!

---

### Post by xen-uno on 2008-07-29
Does the BIOS support booting off a USB CD/DVD drive? I don't think you can boot off the HD with any kind of a bootable CD image (broken down with IsoBuster or otherwise). It's gotta have USB boot support ... how else could you install any OS on it?

---

### Post by jgirata on 2008-07-29
I boot off of USB devices, it's just a matter of getting the Live CD onto the external hard drive, which I don't know how to do.

I did try using Mac's Disk Utility to create a disk image of the Live CD and restoring a partition on my external hard drive with that, but I was getting an error saying that the source could not be validated.

---

### Post by xen-uno on 2008-07-29
You will not be able to do it that way. For instance, the 7.10 Live disk has a couple prog's called wubi-cdboot.exe & start.exe, one or both is a bootable mini OS that are only applicable to a CD based install. Bootable OS disks are not like application disks that you can extract and run. Save your self some grief (not to mention time) and pick up an external optical drive.

---

### Post by OptimisticBear on 2008-07-29
I am currently trying this method right now.

[http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/](http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/)

---

### Post by jgirata on 2008-07-30
> **OptimisticBear said:**
> I am currently trying this method right now.

[http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/](http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/)

Would it be possible to install Ubuntu on a flash drive using that method, then installing it onto the internal hard drive using [this]("http://www.pendrivelinux.com/2008/05/21/usb-xubuntu-804-persistent-install-from-linux/#more-408") method?  The only problem that I can see (not that I'm the expert) is that I can't pull out and re-insert the flash drive, in which case I'd just reboot.

---

