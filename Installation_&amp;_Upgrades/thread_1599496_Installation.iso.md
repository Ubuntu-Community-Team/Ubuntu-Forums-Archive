---
title: "Installation.iso?"
date: 2010-10-17
forum: Installation &amp; Upgrades
---

### Post by 65Hyper on 2010-10-17
Hi, I'm new to Ubuntu, I installed it via Wubi it did well, but when it told me to restart, I did, after restarting I booted Ubuntu Netbook, then it said "Installation.iso not found. This usually happens when your computer does not shutdown correctly, shutdown without unmounting/removing usb. Please run the chkdsk /r" I already ran that many times nothing happens. I have Windows XP Pro 32bit. Any ideas?

---

### Post by efflandt on 2010-10-17
It is impossible to run **chkdsk /f** on a partition you are running Windows from, you have to go to My Computer, right click on your C: drive and in Tools tell it to check the drive and check the box to fix errors if it can, the OK.  Then you have to reboot and let it check the disk.  The only other way to do **chkdsk /f** is to put the disk in an external USB enclosure and do that from another Windows PC.  Not sure if you can do that from a Windows CD or DVD(?).

But I have never done Wubi, so not sure what type of issues you can run into with that, except that I do not think there is a Wubi that has the bugs worked out of it for 10.10 yet.

---

