---
title: "cannot boot fresh installed ubuntu server 16.04"
date: 2016-04-28
forum: Installation &amp; Upgrades
---

### Post by myw714 on 2016-04-28
[TABLE]
[TR]
[TD="class: votecell"][CENTER][COLOR=#6A737C]
[/COLOR]down vote[favorite]("http://serverfault.com/questions/773456/cannot-boot-fresh-installed-ubuntu-server-16-04#")
[/CENTER]
[/TD]
[TD="class: postcell"]I installed ubuntu server 16.04 from a USB stick. At the step of installing GRUB boot loader. I can choose which disk I want to install it.

/dev/sda, is the usb drive.
/dev/sdb, is the hard drive i installed ubuntu. I chose this one.

after installation completed. I removed usb. Now there are 2 options in the boot menu.

first one is Toshiba which is the hard drive I installed ubuntu server. If I use this option to boot, I will get the following error.
"This is a NAS data disk and can not boot system. System halted"

Another option is "ubuntu". if I use this one to boot . It will take me to a screen below. I dont know what to do with it.


[IMG]http://i.stack.imgur.com/1IOCU.jpg[/IMG]

[/TD]
[/TR]
[/TABLE]

---

### Post by gnusci on 2016-05-01
Try with the LiveCD to check with GParted was going on with your partitions.

---

