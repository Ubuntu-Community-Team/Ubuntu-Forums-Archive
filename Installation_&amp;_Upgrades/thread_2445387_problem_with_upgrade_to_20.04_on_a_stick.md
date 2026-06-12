---
title: "problem with upgrade to 20.04 on a stick"
date: 2020-06-13
forum: Installation &amp; Upgrades
---

### Post by praeinf on 2020-06-13
I have installed ubuntu (19.10) on a stick (persistant mode). I receive the message to upgrade to 20.04 but  during 1st part of installation it breaks with message: ubuntu security Realease contains no release-file.
Have any one an idea for help? Thanks

---

### Post by howefield on 2020-06-13
Is it worth troubleshooting when you can create another persistent USB with a fresh download of 20.04 ?

---

### Post by praeinf on 2020-06-13
I use the stick a long time - until now all upgrades were Ok. I want to know why this is difficult to upgrade now.

---

### Post by Adam_GUI on 2020-06-13
I don't understand the thought process here, either.
Why are you looking to upgrade your Live USB stick?
If you have files/settings setup on it, best process would be to back them up, download the 20.04 ISO and create a new Live USB with the usb creation tool in the repos.
It would save you an awful lot of headache in the long run.

---

### Post by C.S.Cameron on 2020-06-14
You can not upgrade the kernel on a Persistent USB stick.
Also the casper-rw file/partition only works on one version of Ubuntu.
Things will go haywire if you try to use it on a newer version.

You can salvage your home directory with all your data and settings.
This is easy if you made the USB using mkusb.
mkusb has a built in home backup feature, look in the usbdata partition.
For a Rufus drive home can be copied using rsync or grsync.
Things are a  little more complex if you used UNetbootin or Universal to make the USB, but it is still possible.

Edit:
Ah Ha! reviewing the posts here, I am wondering if your USB stick has a Persistent install or a Full install of Ubuntu?
A Full install can be worth upgrading , I had upgraded a stick starting from 8.04 for many years, I felt comfortable with GRUB 1.

---

