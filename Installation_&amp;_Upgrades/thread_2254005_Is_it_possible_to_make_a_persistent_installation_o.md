---
title: "Is it possible to make a persistent installation on USB thumbstick?"
date: 2014-11-24
forum: Installation &amp; Upgrades
---

### Post by SagaciousKJB on 2014-11-24
I downloaded Unetbootin and made a Live USB installation of Xubuntu, but I was wondering if it was possible to make a persistent installation and boot it off a thumbdrive in this way?  I'd like to be able to save settings and sessions.

---

### Post by ian-weisser on 2014-11-24
There are two types of 'persistent' installations.

You can install a Live .iso to a USB, with a persistence partition. You can save a limited amount of data and configuration. It's not upgradable.
Details on how to do it are at [https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)

Or you can put a real install of Ubuntu on a USB stick. I have found that USB 3.0 is needed to prevent delays. It's completely configurable and upgradable. It's not a Live environment. It's a real install, and does not use unetbootin.

---

### Post by yancek on 2014-11-24
In addition to the method mentioned above, you have this option with Ubuntu if you download and use unetbootin.  The method mentioned in the link posted above I think is better.

---

### Post by SagaciousKJB on 2014-11-25
> **yancek said:**
> In addition to the method mentioned above, you have this option with Ubuntu if you download and use unetbootin.  The method mentioned in the link posted above I think is better.

I did notice that option, but it didn't seem to do anything.  Is it supposed to be automatic or some kind of user intervention involved?  Perhaps I need to boot the kernel in persistent mode like that link mentioned?

---

### Post by ubfan1 on 2014-11-25
Bug 1159016, Persistence not working for UEFI boots, is still a problem on the live media.  You can fix it by editing the /boot/grub/grub.cfg file and adding the word persistent to the linux lines (like the link shows).

---

### Post by yancek on 2014-11-25
> I did notice that option, but it didn't seem to do anything.  Is it  supposed to be automatic or some kind of user intervention involved?

The only user intervention required is setting the size as the default is set to zero.  You can change it after the system is created to make it larger, usually works.  Don't use UEFI so have no idea about that.

---

### Post by SagaciousKJB on 2014-11-25
> **yancek said:**
> The only user intervention required is setting the size as the default is set to zero.  You can change it after the system is created to make it larger, usually works.  Don't use UEFI so have no idea about that.

Interesting, I don't use UEFI either so I wonder why that bug affects me?  Maybe I'm just expecting the wrong things to be persistent?  Seems like everything is the live default though.

---

### Post by yancek on 2014-11-25
Unetbootin requires FAT32 so you are limited to 4GB files and your persistence cannot be larger than that.  Don't know what you set?  You should be able to modify settings and make system changes as well as save some data, obviously depending upon the size of the flash drive.

---

### Post by sudodus on 2014-11-26
Enter file size (greater than zero) for persistence at the ***[COLOR=#ff0000]red mark[/COLOR]*** in the attached screenshot of Unetbootin. I would recommend at least 1 GB. 4 GB is maximum size.

---

