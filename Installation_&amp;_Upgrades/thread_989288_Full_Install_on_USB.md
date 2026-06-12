---
title: "Full Install on USB"
date: 2008-11-21
forum: Installation &amp; Upgrades
---

### Post by ChrisB111 on 2008-11-21
I have been looking online at installing Ubuntu 8.10 fully on my 16gb usb stick, most of the tutorials on the internet say to manually unplug your hard drive before doing this, I'm not sure if I want to unplug my hard drive, are there any real risks with installing it fully on to a usb stick?

[The tutorial I have been looking at]("http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/")

Thanks,

Chris

---

### Post by oilchangeguy on 2008-11-21
> **ChrisB111 said:**
> I have been looking online at installing Ubuntu 8.10 fully on my 16gb usb stick, most of the tutorials on the internet say to manually unplug your hard drive before doing this, I'm not sure if I want to unplug my hard drive, are there any real risks with installing it fully on to a usb stick?

[The tutorial I have been looking at]("http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/")

Thanks,

Chris

if nothing else, usb sticks are not designed to be hard drive replacements. they do not have the life span of a "normal" hard drive.

also as your link states, unless you unplug the internal drive, the master boot record will be overwritten by grub.

---

### Post by Kevbert on 2008-11-21
- Deleted, double post -

---

### Post by Kevbert on 2008-11-21
They suggest that you disconnect the hard disk so that you can use the guided option. If you choose the manual option you may be able to see the USB as a new drive. You'll need to select it and make a swap file (say 128Mb) and use the rest mounted / and formatted ext3. The problem with this is that flash drives aren't supposed to be used like disk drives as their life is no where near that of a hard disk (same for smart cards etc).
Your better bet is to make the drive persistent, that is that data is written to the drive in one go rather than on the fly as you use it. A better guide is [[COLOR="Red"]this one[/COLOR]]("http://www.pendrivelinux.com/2008/11/01/ubuntu-810-install-using-the-built-in-usb-installer/") for 8.10. I tried a while ago to install usb-creator for 8.0.4.1 without any success.  You'll find speed is nowhere near as good as a hard disk and you may decide that Xubuntu is better (but is still quite slow).

---

