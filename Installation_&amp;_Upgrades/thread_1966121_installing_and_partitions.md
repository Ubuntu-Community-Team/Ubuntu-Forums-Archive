---
title: "installing and partitions"
date: 2012-04-26
forum: Installation &amp; Upgrades
---

### Post by qazxsw21000 on 2012-04-26
The title is a bit vague, but whatever. So I have heard two different things on this subject so I'll ask here. Is it a good idea to put xubuntu on a flash drive or external HDD? If so, which is better? I heard that the HDD is better because of something about moving parts. Which is what I heard makes the HDD a bad choice.

As for partitions. On my external HDD, I have two copies of Linux. The first is Fedora. I tried to put Xubuntu 10.10(?) over it but it installed beside it instead. So will 12.04 give the option to replace Fedora? And weather or not it does, how do I delete the extra partitions and put them back as one big NTFS partition?

---

### Post by oldfred on 2012-04-26
If you want to overwrite existing partitions without resizing then you can use Manual install or Something Else. But if resizing or reformating you should use gparted to adjust partitions. The installer will not let you create NTFS, but you can from gparted on the liveCD.

I have 12.04 on a flash drive, functional, not speedy (more RAM is better, but that is true of all systems). You have to change some settings to reduce writes as flash writes slow and USB is slower than an internal hard drive. With an external hard drive you still lose some due to USB port speed but writes are not as slow as flash.

Install to external drive 11.04. Also any second drive.
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?

---

### Post by qazxsw21000 on 2012-04-26
I will try this out later. The ISO is still downloading. Thanks for the reply.

---

