---
title: "Making a bootable USB in Debian 10 for ubuntu"
date: 2021-04-14
forum: Installation &amp; Upgrades
---

### Post by Hotchilli on 2021-04-14
I have the Ubuntu iso 2.7gb on my Debian 10 desktop l want to install Ubuntu from usb drive
Here is what l did on command line
sudo dd if=/home/Amma/Desktop/ubuntu-20.04.2.0-amd64.iso  of=/dev/sdb2  status=progess oflag=sync

Usb goes not boot

---

### Post by CelticWarrior on 2021-04-14
It needs to be a device, not a partition.

---

### Post by Hotchilli on 2021-04-14
Thanks for post
So please tell me what the command should be please
Or how to make usb bootable

---

### Post by CelticWarrior on 2021-04-14
I meant the output should be to a device - sdb, assuming this is correct -, not to a partition, sdb2.

But you can use a tool for safer results. Using DD and sending it to the wrong drive will irreparably delete everything in there.

[MKUSB]("https://help.ubuntu.com/community/mkusb") can be used in Debian. And [Balena Etcher]("https://www.balena.io/etcher/") is a fully GUI and fool-proof tool.

---

### Post by guiverc on 2021-04-14
I suspect you've already got it solved, but I'll provide some links

Ubuntu: [https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-ubuntu#1-overview](https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-ubuntu#1-overview)

Mac os : [https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-macos#1-overview](https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-macos#1-overview)

windows : [https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-windows#1-overview](https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-windows#1-overview)

FYI:  the same methods will work in Debian as if it's Ubuntu; at worst some Debian packages have slightly different names in my experience, but I use `mkusb` & `dd` on my Lubuntu & Debian (*bullseye*) equally.

---

### Post by hds33 on 2021-04-14
> **guiverc said:**
> I suspect you've already got it solved, but I'll provide some links

Ubuntu: [https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-ubuntu#1-overview]("https://havadurumusorgula.com/sehirler/hatay-hava-durumu/")

Mac os : [https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-macos#1-overview](https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-macos#1-overview)

windows : [https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-windows#1-overview](https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-windows#1-overview)

FYI:  the same methods will work in Debian as if it's Ubuntu; at worst some Debian packages have slightly different names in my experience, but I use `mkusb` & `dd` on my Lubuntu & Debian (*bullseye*) equally.
thank you

---

### Post by C.S.Cameron on 2021-04-16
If you want to boot Ubuntu on that computer, you can boot the Ubuntu ISO from Debian's GRUB:

```
      menuentry "ubuntu-20.04.1-desktop-amd64.iso live-only" {
         set isofile="/ubuntu-20.04.1/ubuntu-20.04.1-desktop-amd64.iso"
         loopback loop (hd0,1)$isofile
         linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject quiet splash maybe-ubiquity nopersistent
         initrd (loop)/casper/initrd
      }
```

Use the correct path to Ubuntu ISO on the desktop.

---

### Post by TheFu on 2021-04-16
The easiest way:  [https://ubuntuforums.org/showthread.php?t=2460347&p=14030825#post14030825](https://ubuntuforums.org/showthread.php?t=2460347&p=14030825#post14030825)

Basically, use the 'cp' command and take advantage of "everything is a file" on Unix systems.  Just be careful to pick the source and target correctly for how you'd like to use the "file" you are writing.  Pick the wrong target and it could be a very bad day.  Please don't overwrite your OS, unless that is truly what you intend.

---

