---
title: "How to edit Master Boot Record"
date: 2007-07-21
forum: Installation &amp; Upgrades
---

### Post by alexv305 on 2007-07-21
I have Ubuntu 7.04 installed. Recently I installed Xubuntu on a second harddrive on the same computer but now Xubuntu starts as the default. i want ubuntu to start as the default...

How do i edit the MBR?

---

### Post by Technoviking on 2007-07-21
Does it still detect your old Ubuntu install? If so just edit your /boot/grub/menu.lst.

Mike

---

### Post by alexv305 on 2007-07-21
See what im trying to do is install Ubuntu without the boot loader. I want it to boot like windows without having to wait on a timer or select any options to boot. Is it possible to do this when making a fresh install or even editing my current one?

Thanks for your help

---

### Post by confused57 on 2007-07-21
You can reinstall Ubuntu's grub IPL to the mbr, using the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

You could add a configfile entry to boot Xubuntu:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
see the section on booting multiple linux distros...also, this link will explain everything you need to know about grub.

---

