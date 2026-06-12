---
title: "Installing from USB stick onto Asus EeePC 1005HAB"
date: 2014-08-03
forum: Installation &amp; Upgrades
---

### Post by Morgan_Parker on 2014-08-03
Good morning,

I'm new to the Ubuntu universe.  After replacing a failing HDD with a 128GB Crucial SSD, I thought I would try reviving my Asus EeePC 1005HAB with a fresh copy of Ubuntu instead of another bloaty Windows install.

This is a netbook so there is no CD/DVD drive - therefore the need to install from a USB stick.  I'm using a generic 1GB USB flash drive and I've loaded the .ISO file onto it using the Universal USB installer Utility.

As far as install goes, I've gotten as far as selecting a time zone - the other times I've powered up and attempted to install I have been plagued with random shut downs.  Could this be an Ubuntu install issue or is it more likely that it is hardware related?

Any thoughts?  Thanks for all your help... I'm excited to get going with Ubuntu!
-Morgan

Netbook details:
ASUS EeePC 1005HA**B**
Intel Atom N270 1.6 GHZ processor
Crucial 128GB V4 SSD (replaced a dying WD 160GB HDD)
1GB RAM

---

### Post by ubfan1 on 2014-08-03
Is 1G really enough for the desktop iso?  I use 2G, and find that the requirement for 1024M free keeps me from using persistence, so you may be a bit tight trying to use 1G without persistence.

---

### Post by Morgan_Parker on 2014-08-03
A very good thought.  I had wondered about this when I read the installation FAQ.  I'll try that first thing this evening.  I guess the other question would be would this cause random shut downs through the installation process?

---

### Post by sudodus on 2014-08-03
```

wc -c ubuntu-14.04-desktop-*.iso
1010827264 ubuntu-14.04-desktop-amd64.iso
1017118720 ubuntu-14.04-desktop-i386.iso

```

Check the size of the pendrive with

```
sudo parted -l
```
Result in MB (10-based)
```
sudo fdisk -lu
```
Result in MB (10-based) and bytes

-o-

So a 1 GB pendrive should be enough, if it is slighly oversized (more  than 1 GB (10-based)), at least if you clone the iso file with ***mkusb***.

See this link [Howto make USB boot drives]("http://ubuntuforums.org/showthread.php?t=1958073")

But it might be a good idea to get a new pendrive, either a cheap, slow but still reliable 4 GB pendrive or a fast USB 3 pendrive. See these links

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[Link to USB 2 and USB 3 speed tests for installers]("http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085")

---

