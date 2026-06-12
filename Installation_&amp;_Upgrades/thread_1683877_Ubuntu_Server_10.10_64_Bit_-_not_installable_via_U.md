---
title: "Ubuntu Server 10.10 64 Bit - not installable via USB"
date: 2011-02-08
forum: Installation &amp; Upgrades
---

### Post by mil ub64 on 2011-02-08
Hi,

I made a bootable USB Stick acording to:
[http://www.ubuntu.com/server/get-ubuntu/download](http://www.ubuntu.com/server/get-ubuntu/download)

with the Universal USB-Installer
[http://www.pendrivelinux.com/downloads/Universal-USB-Installer/Universal-USB-Installer.exe](http://www.pendrivelinux.com/downloads/Universal-USB-Installer/Universal-USB-Installer.exe)

Selecting Ubuntu Server 10.10 64 bit and the correct ISO Image.

The install-USB Stick did boot and start the installation with menu structure an everything. But when it came to copying the files I got a message like:  "Not found on CDROM". Tried it several times.
Is this a known BUG?

With a cd drive which I had to grab from another PC the installation did work properly.

Best regards,
milamber

---

### Post by ikt on 2011-02-08
ops, indeed this is a known issue:

[https://bugs.launchpad.net/ubuntu/+source/cdrom-detect/+bug/582427](https://bugs.launchpad.net/ubuntu/+source/cdrom-detect/+bug/582427)

---

### Post by gordintoronto on 2011-02-08
You could use unetbootin.

---

