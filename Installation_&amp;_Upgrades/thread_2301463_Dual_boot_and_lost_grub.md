---
title: "Dual boot and lost grub"
date: 2015-11-02
forum: Installation &amp; Upgrades
---

### Post by cdric5 on 2015-11-02
Hello,

I wanted to install a dual boot on my machine, with Ubuntu and Windows. I've partionned the pre-installed windows version, and installed Ubuntu on the free space.
However, I am not anymore able to boot on Windows (as well as Ubuntu now :( ). I've used Bootrepair, and here is the log:
[http://paste.ubuntu.com/13083538/](http://paste.ubuntu.com/13083538/)
When I try to repair the grub (recommended repair), here is the message of Bootrepair:
SFS detected. You may want to retry after converting Windows dynamic partitioning (SFS partitions) to a basic disk. This can be performed via tools such as TestDisk or EASEUS-Partition-Master / MiniTool-Partition-Wizard.
Do you want to continue?

What should I do?

Thanks a lot for your help!

---

### Post by yancek on 2015-11-02
> What should I do?

The message you posted tells you what to do.  The SFS means windows proprietary dynamic partitioning and this won't work until you change it.  You can download Testdisk and use it but I would suggest doing some reading on modifying dynamic partitions in windows before trying anything.  Take a look at the post at the link below at the testdisk forums to start.

[http://forum.cgsecurity.org/phpBB3/file-systems-damaged-dynamic-disk-t496.html](http://forum.cgsecurity.org/phpBB3/file-systems-damaged-dynamic-disk-t496.html)

---

