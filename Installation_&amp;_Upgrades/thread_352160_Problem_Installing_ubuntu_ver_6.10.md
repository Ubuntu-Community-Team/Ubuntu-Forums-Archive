---
title: "Problem Installing ubuntu ver 6.10"
date: 2007-02-02
forum: Installation &amp; Upgrades
---

### Post by hd79 on 2007-02-02
I have a Live Distro of Ubuntu from one of the Linux magazines. I am trying to install Ubuntu, but when the DVD boots, and I select either "Install Ubuntu" or I have tried "Start Install in Safe Graphics Mode" I get this screen:

Busy Box v1.1.3(Debian 1:1.1.3-2ubuntu3) Built in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty, job control turned off
(initramfs)_

The cursor just flashes after the initramfs line.

I have tried doing the memory test, and that works ok. The other side of the DVD has Fedora Core ver 6, and that installs ok, but I would really like to try ubuntu, if at all possible.

Thanks for any help you may be able to provide

---

### Post by meng on 2007-02-02
What are the specifications of this machine of yours?
You may need to use the Alternate CD to install Ubuntu.

---

### Post by mrojas73 on 2007-02-03
I get the same error, I have tried the live cd installation and the alternative installation.  They both complete without any errors but the system can't boot, it just get stuck on the ubuntu screen for a while and then eventualy it will go into that black screen with the tty error message.

When I boot with the live cd, the system boot just fine, I run the installer and and after partitioning it tells me that the boot partition will be (hd0) but I only have sata drives wich shows as sda when I do sudo fdisk -l.

The problem is only with edgy, dapper works great but I would like to run edgy.

I figured I would post my problem too, maybe some body knows how to fix it.  I have searched the web and I haven't found a solution to this.

Marco!

---

