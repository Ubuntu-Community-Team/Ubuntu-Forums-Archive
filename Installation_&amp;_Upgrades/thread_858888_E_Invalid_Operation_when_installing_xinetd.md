---
title: "E: Invalid Operation when installing xinetd"
date: 2008-07-14
forum: Installation &amp; Upgrades
---

### Post by wavve on 2008-07-14
Hi,
  I just installed Ubuntu and when I do the following command
sudo apt-get install xinetd, I get the following error

E: Invalid operation.  Does anyone know this means and what I can do to resolve this?

Thanks!

---

### Post by Zed on 2008-07-14
This might sound silly, but try it again. Might you have mistyped 'install' on the command-line and then written it correctly here? apt-get should say 'invalid operation' when you don't give it a command it recognizes like 'install', 'update', 'remove', etc.

---

### Post by saurabhmishra on 2011-05-22
Thanks for helping another newbie!!!

---

### Post by agitato816 on 2011-10-19
> **wavve said:**
> 
E: Invalid operation.  Does anyone know this means and what I can do to resolve this?


I have a same problem!

My stuffs: 
MacBookPro6-2 with Ubuntu 10.10[FONT=Verdana]
iPhone 4 with iOS 5
[/FONT] 
I followed it:
$ mkdir /tmp/packages && cd /tmp/packages
$ wget -nc -c http://archive.ubuntu.com/ubuntu/pool/main/{libi/libimobiledevice/libimobiledevice0_0.9.7-1ubuntu1,libm/libmtp/libmtp-dev_1.0.2-1ubuntu1,libm/libmtp/libmtp8_1.0.2-1ubuntu1,libu/libusb/libusb-0.1-4_0.1.12-14ubuntu0.2,libu/libusb/libusb-dev_0.1.12-14ubuntu0.2}_`dpkg --print-architecture`.deb
$ sudo dpkg --install *.deb
$ sudo apt-get hold libmtp8 libmtp-dev libusb-dev libusb-0.1-4
[FONT=Verdana]
At the last command, I got it:
[B]E: Invalid operation hold
[/B]
Anyone know how to solve this problem?

My iPhone is still not recognized.

[/FONT]

---

