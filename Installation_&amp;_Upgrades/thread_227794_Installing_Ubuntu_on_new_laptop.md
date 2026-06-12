---
title: "Installing Ubuntu on new laptop"
date: 2006-08-02
forum: Installation &amp; Upgrades
---

### Post by vincente on 2006-08-02
I'll be getting my new laptop in few weeks time and it is preinstalled with Windows XP Pro.

I would like to install Ubuntu as a 2nd operating system and i would like to know if it is possible to boot up using the Ubuntu Live CD and using GRUB to partition the drives and eventually install Ubuntu without having to format the laptop and thus keeping my clean Windows XP installation.

Appreciate any help.

---

### Post by nmendham on 2006-08-02
I think you'll need some software like "Drive Partition" or something, to first shrink your Windows partition, and provide room for your linux partition(s).

---

### Post by vincente on 2006-08-02
is grub able to do it?

---

### Post by evaldas on 2006-08-02
grub is boot loader and not partitioning tool. Try to take a look at install guides at [https://help.ubuntu.com](https://help.ubuntu.com), maybe there you'll find something. But I'm almost 100% sure that ubuntu installer's partitioning tool is able to shrink your existing partition to make room for ubuntu.

---

### Post by vincente on 2006-08-02
> **evaldas said:**
> grub is boot loader and not partitioning tool. Try to take a look at install guides at [https://help.ubuntu.com](https://help.ubuntu.com), maybe there you'll find something. But I'm almost 100% sure that ubuntu installer's partitioning tool is able to shrink your existing partition to make room for ubuntu.

thanks for the advice

will try it out when the laptop is here..

---

### Post by amp_man on 2006-08-02
use partition magic or acronis partition manager, they're windows programs that allow you to resize the partition without losing the existing data m(which, afaik, there is no linux tool that can do the same).

---

### Post by JerMe on 2006-08-02
The Ubuntu Dapper Live CD has a partitioner (GParted)  which will allow you to resize your existing NTFS partition.  It's all part of the installation process.

Just do a manual partion of your hard drive.  Shrink your NTFS partition to free up enough space for a root "/" partition for Ubuntu (at least 10GB perhaps), and 512MB for a "swap" partition.  That's it.  Just like any other partitioning scheme, back up your data before you do anything.

---

### Post by Ronbo on 2006-08-02
You can use Gparted Live to  resize and create partitions on your hard drive in order to make room for Ubuntu.  From what I have read it can do just about anything that Partition Magic can do and it doesn't cost a dime.  Just downoad the ISO, burn it to a CD and restart with the CD in the drive.

Check out the web page:

[http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")


Screenshot attached.

---

