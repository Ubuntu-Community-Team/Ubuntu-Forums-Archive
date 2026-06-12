---
title: "persistent USB usage"
date: 2010-05-28
forum: Installation &amp; Upgrades
---

### Post by terranz on 2010-05-28
I would like to know if I can update a live USB version of 10.04

I am, unofficially, running ubuntu 10.04 live USB version from a partition on my 250GB USB HDD at work.

All the apps I use are web bassed except for zeacom and groupwise which I run from a virtual machine I created using virtualbox ose, this machine is one the network running AD and novel and also MS office and uniflow printing

Everything at the moment is running quite well: I tried this a while ago (9.04 or earlier) but I tried enabling update manager and this killed the boot for my live USB and I don't what to risk toying with a system that is running well but I also want to be up to date.

any ideas?

---

### Post by efflandt on 2010-05-28
You can add programs.  But is not wise to do updates on a live iso installation, because it boots from what was in the original iso, before it mounts persistent data.  So things like kernel updates will not work that way, since the new kernel and modules would be unavailable during initial boot.

It is also not secure, because anybody could boot it without a password and get at anything on any connected drives that is not encrypted.

If you have or can create a primary partition for Ubuntu, you could do a regular installation, put grub on that partition, and mark that partition as the only boot partition (with gparted), leaving the standard Windows mbr untouched.  Although, you have to make sure that you use the **Advanced** button in installation summary after setting your user, to put grub where you want it.  I do that on my desktop at home.

For a work laptop which already has 4 primary partitions (Dell recovery and some media thing that can run without Windows) that I do not want to tamper with, I boot Ubuntu from a portable USB hard drive (with grub in its mbr).

---

### Post by terranz on 2010-06-08
Thanks, I've done a propper install to my USB HDD which is working apart from I've lost 3d compositing from moving between computers

---

