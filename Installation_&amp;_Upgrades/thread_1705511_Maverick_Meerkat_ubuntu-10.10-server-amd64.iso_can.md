---
title: "Maverick Meerkat ubuntu-10.10-server-amd64.iso cannot be installed from usb stick"
date: 2011-03-12
forum: Installation &amp; Upgrades
---

### Post by alfonso78 on 2011-03-12
Hello,

I downloaded ubuntu-10.10-server-amd64.iso and tried to install it from an usb stick / pen drive / flash drive.

To prepare the usb stick, first I tried with UNetbootin [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) but I didn't find the server installation in dropdown menu so I chose diskimage, and selected the iso I just downloaded.

The usb stick was bootable but the installation could not find the cdrom ("Cannot find CD"). This is a known issue:
[https://bugs.launchpad.net/ubuntu/+source/cdrom-detect/+bug/582427](https://bugs.launchpad.net/ubuntu/+source/cdrom-detect/+bug/582427)

The best solution (IMO) is this:
[http://ubuntuforums.org/showpost.php?p=9086256&postcount=29](http://ubuntuforums.org/showpost.php?p=9086256&postcount=29)

But even if now there was no more error about the missing cdrom, the installation stopped few seconds after.

I tried also using Universal USB Installer at [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/) which by the way prepares the flash drive so that no cdrom-detect/try-usb=true trick is needed, but again the installation says it cannot find some specific files and aborts.

I also read [https://bugs.launchpad.net/ubuntu/+source/cdrom-detect/+bug/582427/comments/9](https://bugs.launchpad.net/ubuntu/+source/cdrom-detect/+bug/582427/comments/9) that the problem can present itself depending on the usb stick so I tried with two different ones without any luck.

So finally I installed the desktop 32 bit version.

It worked like a charm using Universal USB Installer at first try.

---

