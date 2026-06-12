---
title: "Installing Ubuntu"
date: 2012-09-02
forum: Installation &amp; Upgrades
---

### Post by oldwindows geek on 2012-09-02
Here is mu problem, I am trying to install Ubuntu on a computer that will not read from the cd, will boot to cd, but will not read the disk, it will read the C drive, if I copy the files to a folder on the C drive, how do I, or can I still install Ubuntu that way what file do I have to run, or should I run, and how?

---

### Post by uzumakifahim on 2012-09-02
> **oldwindows geek said:**
> Here is mu problem, I am trying to install Ubuntu on a computer that will not read from the cd, will boot to cd, but will not read the disk, it will read the C drive, if I copy the files to a folder on the C drive, how do I, or can I still install Ubuntu that way what file do I have to run, or should I run, and how?

If you have a computer that don't read CD, then you need to install Ubuntu on that PC using USB drives. Before that you need to install Ubuntu on that USB drive.

---

### Post by oldwindows geek on 2012-09-02
> **uzumakifahim said:**
> If you have a computer that don't read CD, then you need to install Ubuntu on that PC using USB drives. Before that you need to install Ubuntu on that USB drive.
the bios will only boot: floppy, CD or drive C, will not boot USB, currently running windows Xp on it, if I copy the files from the Ubuntu CD to a flash drive, can I then install it through windows that way?

---

### Post by mastablasta on 2012-09-02
if you have a spare  floppy available you can use a small boot loader called PLOP boot manager. 
[http://www.plop.at/en/bootmanager/index.html](http://www.plop.at/en/bootmanager/index.html)

you stick it on a floppy, boot from it and it will give you the option to boot form usb. if you have usb in the slot. so select boot from USB and continue with install.

also clearly it can't boot from CD. it might try to read it and since it can't find the system on it it will go to the next disk in line which is hard disk and boot from that.

1. make sure the downloaded image is good: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
2. make sure your burn is good (verify the data after burn)

ubuntu install looks like this (images): [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

to copy the OS image to USB use the free programmes: unetbootin or linuxliveusb.

---

