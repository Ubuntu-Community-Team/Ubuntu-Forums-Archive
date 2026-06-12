---
title: "Install apps onto a USB stick/drive?"
date: 2016-07-29
forum: Installation &amp; Upgrades
---

### Post by rickblacker on 2016-07-29
Hi.... I'm pretty new to Linux and Ubuntu. I have a little microboard that is running Ubuntu 14.04. The board itself does not have a lot of memory on it.  I have a 64 gig USB memory drive that I'd like to be able to insert into the board and use. I've noticed that when I open the app "Files" I can see the USB stick just fine.  

I'm wanting to install QT the C++ development environment onto the board. In specific, I want to have the USB stick inserted into the board, run the QT installer and have QT installed onto the USB drive.  I'm able to run the QT installer, but when I click to specify where I want it installed, I don't see the USB stick listed, I only see the internal memory location on the physical board. 

Is there a way I can setup Ubuntu and the USB drive such that I can install applications onto this USB drive?

---

### Post by grahammechanical on 2016-07-29
I do not know if that microboard will accept a USB memory stick as storage but I do know that the Linux directory structure will not let you do what you want.

[http://www.thegeekstuff.com/2010/09/linux-file-system-structure/](http://www.thegeekstuff.com/2010/09/linux-file-system-structure/)

All of those directories come off the root directory and are by default on the same partition as the root directory. We can install Ubuntu in such a way that some of those directories are on other partitions. The /home partition is one example. These other partitions would have to be formatted to a Linux file system such as Ext4. But Linux scatters a program's libraries over several directories. This I think will prevent you from doing what you want.

I would guess that the USB memory stick is not formatted to Ext4.

Regards.

---

### Post by QDR06VV9 on 2016-07-29
Moved to Installation & Upgrades for a better fit

---

### Post by rickblacker on 2016-08-05
> **grahammechanical said:**
> I do not know if that microboard will accept a USB memory stick as storage
Yes, it will
> **grahammechanical said:**
> but I do know that the Linux directory structure will not let you do what you want.


[http://www.thegeekstuff.com/2010/09/linux-file-system-structure/](http://www.thegeekstuff.com/2010/09/linux-file-system-structure/)

All of those directories come off the root directory and are by default on the same partition as the root directory. We can install Ubuntu in such a way that some of those directories are on other partitions. The /home partition is one example. These other partitions would have to be formatted to a Linux file system such as Ext4. But Linux scatters a program's libraries over several directories. This I think will prevent you from doing what you want.

I would guess that the USB memory stick is not formatted to Ext4.

Regards.


Thanks for the heads up.  I guess I will have to get creative with how I approach this.  I'm working with ROS and maybe I can get away with at least storing all my development projects and the ROS workspace on the USB drive for storage.

---

