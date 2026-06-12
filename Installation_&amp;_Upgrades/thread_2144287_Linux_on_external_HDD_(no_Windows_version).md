---
title: "Linux on external HDD (no Windows version)"
date: 2013-05-11
forum: Installation &amp; Upgrades
---

### Post by sunfromhere on 2013-05-11
Hello, I plan to install some distros on my external HDD. Now, every single help I've read on the net shows how to do it if you have Windows installed on your internal HDD - which I do not. I have Ubuntu 12.04, **I have no Windows**.

The question is - if I just install Debian (and later, several other distros) on the external HDD following the normal install procedure, don't overwrite Ubuntu's grub, and just do update grub (from Ubuntu) while the E-HDD is plugged in, will I get
a) direct boot to Ubuntu while E-HDD is not plugged in?
b) choice to select a distro while E-HDD is plugged in?
c) a borked grub and possibly not be able to boot Ubuntu?

Thanks for the answers!

---

### Post by Bucky Ball on 2013-05-11
*Thread moved to **Installation & Upgrades***

I take it Ubuntu is on the internal hard drive? If so, other distros to external hard drive, choose 'Something Else' at the partitioning section of the install, or whatever the option might be to partition manually, stick each OSs grub on the same partition the OS is going on, then update grub, as you suggest, on your Ubuntu install on the internal hard drive and the existing grub should pcik up and add your new install on the external drive. 

a) Try it out and see. I imagine you'll get the grub with all entries at boot but if you select anything but the internal Ubuntu install nothing will happen and you'll get an error. Then again, you might get an error immediately at boot regarding the fact that grub can't find the installs on the external.

b) yes.

c) See a). Try it and find out.

---

### Post by sunfromhere on 2013-05-11
Thanks for a fast answer! Yes, Ubuntu is on the I-HDD. :)

If I bork grub, it should be fixable using the Ubuntu live USB and just reinstalling grub?
If grub is installed on the E-HDD, and the computer is set to boot from the I-HDD, wouldn't it ignore the grub on the E-HDD? Hmm...

This will be a very interesting experiment!

---

### Post by grahammechanical on 2013-05-11
Just to confirm what you have already worked out.

1) When you install Linux to the external HDD make sure that Grub is installed on the external HHD (sdb) and not on the internal HDD (sda). Do this for every installation of Linux.

2) After each installation boot into Ubuntu (internal HDD) and run these two commands

```
sudo grub-update
```
```
 sudo grub-install /dev/sda
```

In this way the Ubuntu grub (internal HHD) will detect each installation and you will be able to boot to it from Ubuntu grub.

This link is a bit old but look at the images

[http://www.linuxbsdos.com/2011/05/04/manual-disk-partitioning-guide-for-ubuntu-11-04/](http://www.linuxbsdos.com/2011/05/04/manual-disk-partitioning-guide-for-ubuntu-11-04/)

See the second image - Allocate drive space? Do you see the panel Device for boot loader installation? It defaults to sda but if you click on it you will see sdb. You select sdb. Got it?

If boot priority is set to internal HDD then you will load Ubuntu by default whether the external HDD is plugged in or not. Of course, if the external HDD is not plugged in then you will get an error if you try to boot any of the installations on the external HDD.

The last Linux installed will put its boot loader into MBR external HDD and also detect all the others including Ubuntu. So, if you ever disconnect the internal HDD you can boot into the external HHD and still get a Linux loading.

There is one area that I noticed when I put in a second hard disk and installed Ubuntu onto it. The installation process used the swap partition on the first hard disk. This meant that if ever the first hard disk failed then Ubuntu on the second hard disk would not have a swap file. To overcome this I disconnected the first hard disk and re-installed. Now because I have a swap file on the second disk any new installation of Ubuntu will latch on to that swap partition and not the swap partition on the first hard disk.

Regards.

---

### Post by sunfromhere on 2013-05-11
Thanks for the detailed answer! When I'm finished I'll post here how it went, hopefully without problems :)

---

### Post by Bucky Ball on 2013-05-11
> **grahammechanical said:**
> 
```
sudo grub-update
```


Agree with all but not sure that you need to reinstall grub to sda after every install on the external and grub update on the internal. Negates updating grub if you then reinstall it. The reinstall will update grub anyway.

I've never had to do this, only 'sudo update-grub'.

---

### Post by sunfromhere on 2013-05-17
Hello, I am writing this from my freshly installed Debian on sdb. Everything went without issues. I didn't update Ubuntu's grub, because it works well this way: if I just turn on the computer, it will load Ubuntu. I installed Debian's grub on sdb, so now when I want Debian, I just plug in E-HDD and then select boot from E-HDD. :)

---

### Post by Bucky Ball on 2013-05-17
Excellent. If you consider this solved, to help others, please mark it that way by editing first post, Go Advanced, and change the title prefix to [SOLVED]. Thanks.

---

