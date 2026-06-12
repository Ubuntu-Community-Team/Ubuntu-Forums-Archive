---
title: "Backing up current OS and dual booting with Ubuntu"
date: 2014-12-22
forum: Installation &amp; Upgrades
---

### Post by maika2 on 2014-12-22
The first time I installed Ubuntu on a computer, with the intention of dual booting, I *accidentally* overwrote the operating system that was on it. I love Ubuntu, and now I want to install it on another machine. Is there a way of backing up the computer's current OS (Windows 8) using USB or a DVD, or some other way of implementing a figurative "safety net"? If you have any ideas, I'd love it if you'd let me know. Thanks guys.

---

### Post by Mark Phelps on 2014-12-22
>  Is there a way of backing up the computer's current OS (Windows 8) using USB or a DVD 

Using DVD, no.  Typical Win8 installations run into the tens of Gigabytes, whereas a DVD only stores a little over 4.5 GB.

You CAN do this to a USB stick if it is large enough.  You would be looking at a 32GB or 64GB USB stick -- depending on the size of your Windows partitions.

The best tool I've used to backup/restore of Windows systems is Macrium Reflect -- and you can download it and use it for free.

When you go to do the backup, choose the option that says to backup the partitions that allow you to restore the OS.  That will require 2 partitions, maybe more.

Also choose the option to create a Linux Boot CD/USB.  You would need that if you later need to restore from the backup.

---

