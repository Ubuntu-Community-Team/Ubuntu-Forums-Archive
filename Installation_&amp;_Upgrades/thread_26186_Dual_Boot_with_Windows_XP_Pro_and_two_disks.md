---
title: "Dual Boot with Windows XP Pro and two disks"
date: 2005-04-12
forum: Installation &amp; Upgrades
---

### Post by sp3tt on 2005-04-12
I want to install Ubuntu together with XP Pro. The machine has two disks, and Windows is installed on the primary.
If I install Ubuntu on the secondary HDD, it won't mess with my Windows disk, right?
I have heard that people have problems with the boot loader, GRUB. What causes these problems, and how do I avoid getting them? I would like to be able to boot both Win XP and Ubuntu as soon as the install is finished.

Is there a guide to dual boot I might want to read?

---

### Post by orion_114 on 2005-04-12
Try this post ....
[http://ubuntuforums.org/showthread.php?t=16287](http://ubuntuforums.org/showthread.php?t=16287)

 Also check out these links ...
[http://www.ubuntuguide.org/](http://www.ubuntuguide.org/)
[http://www.ubuntuforums.org/showthread.php?t=25991&highlight=Dual+Boot](http://www.ubuntuforums.org/showthread.php?t=25991&highlight=Dual+Boot)
[http://www.troubleshooters.com/linux/grub/grub.htm](http://www.troubleshooters.com/linux/grub/grub.htm)

Hope that helps ? ;)

---

### Post by sp3tt on 2005-04-12
After reading the grub guide, I wonder, is grub fully installed with ubuntu?
And for my system, the configuartion file would look like this:

> title  Windows XP Pro
root (hd0,0)
kernel (What's the path for windows?)

title  Ubuntu
root (hd1,0)
kernel /boot/vmlinuz-2.6.7 root=/dev/hda1

---

### Post by rotorwash on 2005-04-12
Take a look at [this](http://software.newsforge.com/article.pl?sid=05/02/15/2023237&from=rss)  article on NewsForge. The article show you how to do what you want, that is, if  you want to use the windows boot loader (NTloader) to boot.

---

### Post by sp3tt on 2005-04-13
[QUOTE=rotorwash]Take a look at [this](http://software.newsforge.com/article.pl?sid=05/02/15/2023237&from=rss)  article on NewsForge. The article show you how to do what you want, that is, if  you want to use the windows boot loader (NTloader) to boot.[/QUOTE]
 Wow, that is one simple way of getting a dual boot system!
Now to wait for the Ubuntu CDs to arrive...

Oh, just one more thing, is there a nice all-on-one-page-installation guide available, so I can print and read it?

EDIT: My two disks are SATA disks, does it make a difference?

---

### Post by noelferg on 2005-04-14
[QUOTE=sp3tt]

is there a nice all-on-one-page-installation guide available, so I can print and read it?

See this - [http://mrbass.org/linux/ubuntu/install/](http://mrbass.org/linux/ubuntu/install/)

---

