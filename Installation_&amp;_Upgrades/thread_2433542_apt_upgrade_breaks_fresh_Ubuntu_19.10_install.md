---
title: "apt upgrade breaks fresh Ubuntu 19.10 install"
date: 2019-12-20
forum: Installation &amp; Upgrades
---

### Post by dreweinhorn on 2019-12-20
I have a fresh install of 19.10 on my laptop.

It would not successfully reboot after the reboot required to finish upgrade.

I took me a while to figure out that I was habitually doing:

sudo apt update
sudo apt upgrade

based on experience with earlier Ubuntu installations and this is what broke the system.

Currently the Ubuntu Software gui tool says the "Software is up to date".

But, apt list --upgradabable says:

drew@drew-ThinkPad-T520:~$ apt list --upgradable
Listing... Done
gzip/eoan-updates 1.10-0ubuntu3.1 amd64 [upgradable from: 1.10-0ubuntu3]
libpam-modules-bin/eoan-updates 1.3.1-5ubuntu1.19.10.0 amd64 [upgradable from: 1.3.1-5ubuntu1]
libpam-modules/eoan-updates 1.3.1-5ubuntu1.19.10.0 amd64 [upgradable from: 1.3.1-5ubuntu1]
libpam-runtime/eoan-updates,eoan-updates 1.3.1-5ubuntu1.19.10.0 all [upgradable from: 1.3.1-5ubuntu1]
libpam0g/eoan-updates 1.3.1-5ubuntu1.19.10.0 amd64 [upgradable from: 1.3.1-5ubuntu1]
ubuntu-desktop-minimal/eoan-updates 1.440.1 amd64 [upgradable from: 1.440]
ubuntu-desktop/eoan-updates 1.440.1 amd64 [upgradable from: 1.440]
ubuntu-minimal/eoan-updates 1.440.1 amd64 [upgradable from: 1.440]
ubuntu-standard/eoan-updates 1.440.1 amd64 [upgradable from: 1.440]
update-notifier-common/eoan-updates,eoan-updates 3.192.26.1 all [upgradable from: 3.192.26]
update-notifier/eoan-updates 3.192.26.1 amd64 [upgradable from: 3.192.26]
drew@drew-ThinkPad-T520:~$

If I do a sudo apt upgrade all these updates are installed

But, the next reboot hangs

with: ubuntu followed by an row a ubuntu icon as a superscript with 5 dots below that cycle from red to white this never moves on to a login prompt.
I'm assuming it's the libpam stuff that's breaking the system.

Obviously there is stuff going on here that I don't understand.

---

### Post by mörgæs on 2019-12-22
It seems to be related to a Thinkpad T520 but let's see the hardware details anyway. Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

