---
title: "installing ubuntu on usb drive"
date: 2011-05-02
forum: Installation &amp; Upgrades
---

### Post by gkman10 on 2011-05-02
hello.

I have never used ubuntu before- but i would very much like to.

however i have a bit of a problem installing ubuntu on my hard disk and I would like to install it on a usb drive.

I had ubuntu 10.10 desktop live cd (no internet connection) and a 8 GB usb flash drive and I tried following this guide:[URL="http://www.instructables.com/id/Boot-and-Run-Ubuntu-from-a-Flash-Drive/"]
 http://www.instructables.com/id/Boot-and-Run-Ubuntu-from-a-Flash-Drive/[/URL]
but i got confused  and error messages.

then I tried just using the regular installing wizard. but it keeps getting stuck towards the end (when it say's "ready when you are")

now i am downloading the new version (11.04) cd (desktop) and dvd.

can anyone help?

---

### Post by mörgæs on 2011-05-02
Hi, welcome to the fora.

Best is to stick to 10.10 at least for a month.

When writing your user name, do you get a green check mark?

---

### Post by gkman10 on 2011-05-03
mörgæs, thanks for the response.

yes I have got a green check next to the user name.
however I tried using the install wizard with 11.04 and it has worked and install successfully onto the USB drive.

now I am just trying to configure it to be able to run on different machines without any trouble of drivers and etc.

also I am trying to figure out how to install programs such as Alien without any internet connection.

is there any site you can recommend that teaches to do stuff like that in Ubuntu for newbies like me you would recommend?

---

### Post by oldfred on 2011-05-03
Example of install to USB flash or SSD. A lot of the configuration for flash is the same as SSD, just that flash is a lot slower than SSD.

It does not have to be encrypted:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)

Use ext2 or ext4 without journal:
tune2fs -O ^has_journal /dev/sda1
No swap or set swapiness
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler

You want journal to speed up system recovery if you have to do repairs or run fsck. But if partition is small then it does not take long to fsck anyway and without journal writing is reduced.
SSD’s, Journaling, and noatime/relatime 
[http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/](http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/)
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)

---

