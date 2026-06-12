---
title: "How to get Ubuntu Netbook Edition install on an usb stick ?"
date: 2010-12-08
forum: Installation &amp; Upgrades
---

### Post by eeepc900a on 2010-12-08
I own an eee pc 900a and would like to install  [http://releases.ubuntu.com/lucid/ubuntu-10.04-netbook-i386.iso](http://releases.ubuntu.com/lucid/ubuntu-10.04-netbook-i386.iso) to it. 

The eee pc hasn't got an CDROM drive so I have to convert the iso file  to an img file to get it on an usb stick for installation.

This page describes how to do that with [http://www.ubuntu.com/netbook/get-ubuntu/download](http://www.ubuntu.com/netbook/get-ubuntu/download)
with Windows, Mac or Ubuntu using usb-creato. But I have non of these available.

How can I convert the iso to an USB image with the help of debian ?

---

### Post by sikander3786 on 2010-12-08
Welcome to the forums :-)

You can download the Linux version of Unetbootin and it'd definitely run on Debian.

[http://unetbootin.sourceforge.net](http://unetbootin.sourceforge.net)

Or see this.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by Skaperen on 2010-12-08
> **eeepc900a said:**
> How can I convert the iso to an USB image with the help of debian ?
Pretty much everything that runs on Ubuntu runs on Debian and visa-versa.  And that mostly goes for all the major Linux distributions.  In many cases you can have success even on BSD and other Unix systems (build programs from source or get binaries for that specific system).

Maybe one of these days Ubuntu will make its ISO images also be hard drive bootable, too.  Then you can just cat or dd the image to a USB flash drive.

---

