---
title: "Live usb ubuntu server."
date: 2014-07-26
forum: Installation &amp; Upgrades
---

### Post by bob40 on 2014-07-26
I have been trying like the devil to make a usb stick that will run, not install, ubuntu server.  I used the Setup Disk Creator but never see the "try" option.  I think I finally realized that this option is only on the desktop version.

Two questions:
1. Can I make a USB stick RUN Ubuntu server?

2. Even if I do use the desktop version, will I have to select "try" every time I boot it?

Thanks,
Bob

---

### Post by sudodus on 2014-07-26
Yes, you can ***install*** it to a USB drive, pendrive, HDD or SSD :-)

The computer and linux operating systems consider all these drives to be mass storage devices and treat them in the same way, so it is straight-forward. What computer is it, and which version of Ubuntu server do you want to install (32-bit or 64-bit, 12.04 LTS or 14.04 LTS)?

See this link and links from it:[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

---

### Post by bob40 on 2014-07-26
> **sudodus said:**
> Yes, you can ***install*** it to a USB drive, pendrive, HDD or SSD :-)

The computer and linux operating systems consider all these drives to be mass storage devices and treat them in the same way, so it is straight-forward. What computer is it, and which version of Ubuntu server do you want to install (32-bit or 64-bit, 12.04 LTS or 14.04 LTS)?

See this link and links from it:[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

I have a lenovo laptop that has Ubuntu desktop on the HD.  I want to be able to run server off of a usb stick.  Both versions are 14.04 64 bit.

Also, is there a difference between a "live CD" and an install CD?  If so, how do I get the live?

---

### Post by sudodus on 2014-07-26
A CD cannot run an installed system (unless you have a read/write CD disk and a very special file system). The kind of installer there is for the server does not run a live system, it only installs, but as I wrote is post #2, you can install into a USB drive, and I'll add: from a CD or from another USB drive.

It will be easier to perform the installation, if you remove the internal drive, but if you are careful, you will succeed even with the internal drive connected. Select manual partitioning and start a second screen with ***ctrl + alt + F2***, where you can run some commands to identify the drive

```
sudo parted -l
```
or if it is not available (I don't remember which commands are available at that stage of the installation)
```
sudo fdisk -lu
```
and
```
df
```

You get back to the installer's menus with ***ctrl + alt + F1***

---

### Post by ian-weisser on 2014-07-27
> **bob40 said:**
> 1. Can I make a USB stick RUN Ubuntu server?

Yes, but it is long and arduous to do so. And it may not do what you expect. For example, the content you wish to serve won't be included, nor will any automatic way of loading the content from some read/write source.

An installed version of Ubuntu isn't designed to run read-only. It took *years*  of development to kludge a working Ubuntu system snapshot into a  read-only, compressed binary format, and to successfully decompress it in  RAM into a working system again. When you play with the LiveUSB image, you're merely packing around the edges - you can't change that binary shapshot. You must duplicate all the effort to create a fresh snapshot of complete, exact system you want to run.

And it won't solve your server's security problem. The running processes on a read-only system are still exploitable. The compromised application will be restored after a reboot, of course...but it's better to keep your applications up to date with security fixes instead of letting them pollute the internet for weeks until you notice and reboot. Including security fixes on a Live image means maintaining and updating that system image withsecurity updates, and replacing the system snapshot on the USB stick periodically.

It's a _lot_ less work to simply install an ordinary Ubuntu server, secure it properly, and maintain it properly.


A better question might be 'Can I create an Ubuntu-based read-only server that runs from a customized Live USB stick?'

Yes, see [http://live.debian.net](http://live.debian.net)
It's not easy, and it has a learning curve, but it's a lot easier than what you were asking for. And it's much easier to maintain.

---

### Post by gordintoronto on 2014-07-27
Apparently you missed the suggestion to INSTALL Ubuntu Server onto a USB stick. At that point, it's just like running from a hard drive, but slower. If you have a data drive, it's easy to auto-mount it by modifying fstab.


> **ian-weisser said:**
> Yes, but it is long and arduous to do so. And it may not do what you expect. For example, the content you wish to serve won't be included, nor will any automatic way of loading the content from some read/write source.

An installed version of Ubuntu isn't designed to run read-only. It took *years*  of development to kludge a working Ubuntu system snapshot into a  read-only, compressed binary format, and to successfully decompress it in  RAM into a working system again. When you play with the LiveUSB image, you're merely packing around the edges - you can't change that binary shapshot. You must duplicate all the effort to create a fresh snapshot of complete, exact system you want to run.

And it won't solve your server's security problem. The running processes on a read-only system are still exploitable. The compromised application will be restored after a reboot, of course...but it's better to keep your applications up to date with security fixes instead of letting them pollute the internet for weeks until you notice and reboot. Including security fixes on a Live image means maintaining and updating that system image withsecurity updates, and replacing the system snapshot on the USB stick periodically.

It's a _lot_ less work to simply install an ordinary Ubuntu server, secure it properly, and maintain it properly.


A better question might be 'Can I create an Ubuntu-based read-only server that runs from a customized Live USB stick?'

Yes, see [http://live.debian.net](http://live.debian.net)
It's not easy, and it has a learning curve, but it's a lot easier than what you were asking for. And it's much easier to maintain.

---

