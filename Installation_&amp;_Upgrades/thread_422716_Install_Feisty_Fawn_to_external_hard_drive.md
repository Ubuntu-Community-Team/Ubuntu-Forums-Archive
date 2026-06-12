---
title: "Install Feisty Fawn to external hard drive"
date: 2007-04-25
forum: Installation &amp; Upgrades
---

### Post by xintol on 2007-04-25
Hello Everyone, I am a greenhorn to Linux. I have find this great OS Feisty Fawn 7.04 and had download it to my desktop (in window xp). I have a 300GB external hard disk drive which I use to backup files from my desk top and laptop, and I would like to install Feisty to it. I have read some tutorials and guides, but I have not find a tread that show me how to make a live CD and install to external HDD. Please help :)

---

### Post by diyroberts on 2007-04-25
I'm currently trying to do the same thing!

I'm downloading the iso file, which I know how to get onto a bootable CD, where next is my question?!

Cheers
Will

---

### Post by diyroberts on 2007-04-25
Sorry to post again! But will this guide be useful?

[http://www.pendrivelinux.com/2007/01/25/usb-x-ubuntu-610](http://www.pendrivelinux.com/2007/01/25/usb-x-ubuntu-610)

Cheers
Will

---

### Post by xintol on 2007-04-25
Thanks for the links. The USB-HDD and pen drive is almost the same, but I am nervous about the fdisk. I have a lot of data in it. If I mess up, I may loss all my data. Can I combine the procedure for fdisk a USB and dual-boot to fdisk my USB-HDD.

---

### Post by amgadpasha on 2007-05-06
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/casper/+bug/84591](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/84591) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				ok, i think this method will not work with hard disks, it'll probably work with flash disks only, and for sure will not work with feisty, as this [bug]("https://bugs.launchpad.net/ubuntu/+source/casper/+bug/84591") broke the persistent mode that this method relies on
the problem am having with my western digital external usb hard disk, is that it seems i can't boot from it, the bios gives option to boot from usb storage device when its attached, but nothing happens after that..
what am thinking about is to install the system on the external HD using the live cd as usual, but using a usb flash drive to be mounted as /boot , so that grub can run from the flash, and edit the grub config files to load the system from the external HD.. am guessing this would work some how, and it is my only solution to install ubuntu in my work laptop. but i have no idea how to do it exactly, and will welcome any help

---

