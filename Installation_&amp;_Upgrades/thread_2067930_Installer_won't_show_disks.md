---
title: "Installer won't show disks"
date: 2012-10-08
forum: Installation &amp; Upgrades
---

### Post by nijmegen96 on 2012-10-08
Hi there
I'm new to linux and I can't get it installed. I was originally going to install linux mint but I had the same problem with Ubuntu. I'll explain in a moment. My computer is a Dell Optiplex GX520. 

Here are a few quick specs:

Pentium 4 HT 2.8Ghz
1 GB of ram
160 GB HDD (there is an 80 GB partition with Windows XP installed and the rest is just free space)
CD Drive (No DVD)

So the problem is that the installer won't show any disks. This has happened to me with Linux Mint 13, Linux Mint 12, and Ubuntu 12.04. I have tried everything. I even thought that my boot loader was effecting it somehow. I don't have a DVD drive so the install disc is either on a usb flash drive or a 700MB CD. The Disk Utility does show all the disks though. I'm starting to think its my hardware thats incompatible or something.

I posted in the Linux Mint forums as well, however its been two days and nothing.


Does anyone here have a suggestion?

---

### Post by albandy on 2012-10-08
In order to discard a kernel 3.2 problem, can you try to boot with ubuntu 10.04 ?

[http://releases.ubuntu.com/lucid/ubuntu-10.04.4-desktop-i386.iso](http://releases.ubuntu.com/lucid/ubuntu-10.04.4-desktop-i386.iso)

---

### Post by darkod on 2012-10-08
If the disk utility and gparted are showing the disk OK but the installer not, usually that means the disk has been used in fakeraid before and has meta data remains. In that case the installer ignores it thinking it might be part of a raid array.

If you ARE NOT running raid, boot the ubuntu cd in live mode, open terminal and try:
sudo dmraid -Er /dev/sda

If it asks you to confirm removing meta data, probably that was the issue. Just confirm and you should be able to install fine.

---

### Post by nijmegen96 on 2012-10-08
Alright the command worked. Thanks a bunch.

---

