---
title: "Grub Menu - How many items?"
date: 2010-01-06
forum: Installation &amp; Upgrades
---

### Post by boosterjet on 2010-01-06
Hi,
Just had an upgrade installed by the upgrade manager. My grub menu now has another two lines added forcing me to make a default change. Here is a copy of the grub menu

john@john-desktop:~$ grep "menuentry" /boot/grub/grub.cfg
[B]menuentry "Ubuntu, Linux 2.6.31-17-generic" {
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)"[/B] {
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
menuentry "Memory test (memtest86+)" {
menuentry "Memory test (memtest86+, serial console 115200)" {
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
john@john-desktop:~$ 

Do I need all these entries? If not what should I delete and how do I do it? 
:confused:

---

### Post by m0o on 2010-01-07
You can uninstall old kernels if you aren't using them for a particular reason. Here's a nice guide on [how to clean up unused old kernels]("http://www.unixmen.com/linux-tutorials/659-how-to-uninstall-the-old-kernels-in-ubuntu"). This should clean up your Grub also.

---

### Post by Sef on 2010-01-07
> You can uninstall old kernels if you aren't using them for a particular reason.

It is best to keep one older kernel around in case there is a problem with the current kernel.

---

### Post by boosterjet on 2010-01-07
Thanks it looks like a reasonably easy fix.

---

