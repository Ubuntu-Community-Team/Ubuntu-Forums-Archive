---
title: "can i Install ubuntu without CD or USB?"
date: 2014-09-05
forum: Installation &amp; Upgrades
---

### Post by hai3 on 2014-09-05
I have installed ubuntu through wubi. It is too slow on my ultra-low end PC. I'm going to uninstall it. 
How do I install real Ubuntu 13.04 without USB or CD? My stupid DVD drive is too bad, it only cost $5. I have destroyed 5 R CD. It is not RW so i can't get space back after formatted.
I only have a 512MB USB, i cant do anything with it.

---

### Post by yancek on 2014-09-06
I'm not sure if that is a typo in your post, 13.04.  If that is the version you have, it is not supported and it will be very difficult to install any software or get any updates.  The current supported versions are 12.04 and 14.04.  With only 512MB of RAM you might try one of the derivatives like Lubuntu or Xubuntu.

Also, wubi isn't supported any longer although it still might work on some systems.  I would expect it would be very slow on your hardware.

You could download the iso file and boot it from your hard drive and install it but, that only works if you already have a system installed with Grub or Grub2 bootloader.  Since you don't seem to have anything on the machine that does not seem like a possibility.  The netinstall option at the link below might be worth checking out.

 [http://www.ubuntu.com/download/alternative-downloads](http://www.ubuntu.com/download/alternative-downloads)

---

### Post by gdesilva on 2014-09-06
Try Unetbootin - this is a product which will enable you to install most Linux OSs.

---

### Post by sudodus on 2014-09-06
> **hai3 said:**
> I have installed ubuntu through wubi. It is too slow on my ultra-low end PC. I'm going to uninstall it. 
How do I install real Ubuntu 13.04 without USB or CD? My stupid DVD drive is too bad, it only cost $5. I have destroyed 5 R CD. It is not RW so i can't get space back after formatted.
I only have a 512MB USB, i cant do anything with it.

Yes, you can boot from a 512 MB pendrive :-) if the computer can boot from USB. Download ***Ubuntu 14.04 mini.iso ***(alias netboot). It is only 31 MB. You can install it into your USB pendrive.

Boot the computer from the mini.iso pendrive and install 'any' Ubuntu system from it, if you have a wired internet connection.

See these links

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)[URL="http://ubuntuforums.org/showthread.php?t=2130640"]
Old hardware brought back to life[/URL]
[http://cdimage.ubuntu.com/netboot/14.04/](http://cdimage.ubuntu.com/netboot/14.04/)

Try to install it with ***Unetbootin***! Come back with more questions, if you need help to get it running!

In that case, ***please specify your computer***. It makes it easier to give good advice. Your computer will probably run better with another flavour of Ubuntu: Lubuntu with an ultra light desktop environment or Xubuntu with a medium light desktop environment.

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

I guess from your opening post, that you are running Windows now. Windows XP?

*Edit*: Wubi and 13.04 are no longer supported, so it is a good idea to make a real installation of a current version. See these links
[Forums Staff recommendations on WUBI]("http://ubuntuforums.org/showthread.php?t=2229766")
[Forums Staff recommendations on EOL Ubuntu releases, in particular 10.04 desktop.]("http://ubuntuforums.org/showthread.php?t=2229730")[URL="http://ubuntuforums.org/showthread.php?t=2230389"]
Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it[/URL]

---

### Post by hai3 on 2014-09-06
Thanks everyone! I have Windows 7 and im gonna borrow a 2GB USB ... Will it work?

---

### Post by EuclideanCoffee on 2014-09-06
> **hai3 said:**
> Thanks everyone! I have Windows 7 and im gonna borrow a 2GB USB ... Will it work?

2GB usb will be enough. You can install Unetbootin on your Windows 7 machine. Download the regular 14.04.1 image from ubuntu.com. And format your usb. Set it with Ubuntu 14.04.1 and then restart your computer. Boot from USB. There you go. :mrgreen:

---

### Post by hai3 on 2014-09-06
How do I create a partition using Computer manager on windows 7 for ubuntu?

---

### Post by sudodus on 2014-09-07
I guess you want to dual boot. See this link for details

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by Mark Phelps on 2014-09-07
Just so you know, a Wubi install does not run noticeably slower than a regular install, so, if it's too slow now, it will be much the same when you install it to its own partition.

With that little memory, and a low-end machine, you need to consider something like Lubuntu, instead.

---

### Post by hai3 on 2014-09-07
LOL.
here is my PC specs:
CPU: Core i3 3240 3.4 GHZ
RAM: 1x4 GB
GPU: Intel HD Graphics 1000 desktop 64MB
I called it low-end PC because an Ultra-low end PC can run Crysis while i cant.

How do I boot the ISO file without USB or CD? 
and how do i create partition without destroy my hdd?

EDIT: I am new to Linux. I wasnt knew what is an operating system until everyone ask me to swicth to Linux. Im only 13 yrs old

---

### Post by uRock on 2014-09-07
You will need to shrink your current Partition within Windows. [http://technet.microsoft.com/en-us/magazine/gg309169.aspx](http://technet.microsoft.com/en-us/magazine/gg309169.aspx)

As mentioned earlier, Unetbootin can get the installer started without using a USB or DVD. [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by hai3 on 2014-09-07
> **uRock said:**
> You will need to shrink your current Partition within Windows. [http://technet.microsoft.com/en-us/magazine/gg309169.aspx](http://technet.microsoft.com/en-us/magazine/gg309169.aspx)

As mentioned earlier, Unetbootin can get the installer started without using a USB or DVD. [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

how do i get Unetbootin to get the installer work?

---

### Post by uRock on 2014-09-07
Last sentence in step three of the above link.

---

### Post by andrew102 on 2014-09-07
Actually, automatic resizing of partitions is available within the installer itself - usually works for me with Win7 [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by hai3 on 2014-09-08
Are there any tutorial for newbie to install Ubuntu through Unetbootin without destroyting hdd?

---

### Post by yancek on 2014-09-08
What you initially described is referred to a a 'frugal install' which the link below describes.   If you have obtained a flash drive to use, that would be better and instructions on creating a bootable flash drive with unetbootin are on their page, second link below.  If that isn't detailed enough, just google as there are a lot of tutorials on it.  If you are going to use windows 7, make sure you download the windows version of unetbootin.

[http://www.my-guides.net/en/guides/linux/how-to-install-linux-from-windows-using-unetbootin](http://www.my-guides.net/en/guides/linux/how-to-install-linux-from-windows-using-unetbootin)

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by sudodus on 2014-09-09
There is a good tutorial for Unetbootin at this link

[Paul Sutton's Unetbootin how to]("http://zleap.net/unetbootln-usb-how_to/")

and there is general information at the following links

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

[Dual Boot with Windows]("https://help.ubuntu.com/community/WindowsDualBoot")

---

### Post by hai3 on 2014-09-12
Thanks!

---

