---
title: "Ubuntu server installation failed"
date: 2012-01-13
forum: Installation &amp; Upgrades
---

### Post by TheArchedOne on 2012-01-13
Hi,

I'm having problems installing Ubuntu 11.10 server on a new HP proliant microserver. I'm trying install from one bootable USB stick (created using the USB installer from pendrivelinux.com) to another USB stick (2GB). I get as far as the "Select and install software" stage and at about 85% complete I get an "installation step failed" error. I've tried recreating the bootable stick. I've tried downloading the iso again, but it fails every time. Does anyone know what's happening here and what I can do to fix the issue?

Thanks in advance

TAO

---

### Post by Cheesemill on 2012-01-14
I shouldn't think that 2GB is enough room to install Ubuntu Server.

---

### Post by darkod on 2012-01-14
Even though the finished install is about 1.7GB I would agree 2GB is quite limited. Also don't forget, to be exact, the finished install is 1.7GiB while a usb stick of 2GB has about 1.8GiB.

Can't you simply create a 10GiB partition on your hdd(s) and use it as root?

That's what I did on my HP Microserver. A 10GiB / partition, and the rest as /data partition. But the ubuntu server version I used is 10.04.3 LTS because I wanted an LTS.

---

### Post by TheArchedOne on 2012-01-14
Thanks guys. I tried an 8GB stick and it works fine.

---

