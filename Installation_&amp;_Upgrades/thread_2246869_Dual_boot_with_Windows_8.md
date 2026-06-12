---
title: "Dual boot with Windows 8"
date: 2014-10-03
forum: Installation &amp; Upgrades
---

### Post by gordoha on 2014-10-03
Over the years I have installed ubuntu many times, but have not done so in two years.  I am now trying to install it on my business partners laptop which has windows 8 which we both hate.

I downloaded the latest ubuntu.

The only direction after that are how to boot from DVD or from a USB.  I dont want to do that.  I want to partition the drive and install it on half the drive.

cicking around on the dowload it did it started to install apparently but said it was downloading again and would take 40 minutes.  I walked away and came back to a blank desktop.

I guess I just dont know what i am doing.

I seemingly recall step by step instructions in prior years, but I cant find them anywhere now.

Can someone point me to a basic guide to what I need to do here (cant find question mark, am on spanish keyboard)

I dont want to boot from USB.  I want to partition the drive.

thanks

---

### Post by yancek on 2014-10-03
The best tutorial I've seen on installing Ubuntu 14.04.  You can partition the hard drive from the installation medium whether it is a DVD (the iso file is too large for a CD) or from a flash drive.  You could also download it and boot it directly from the hard drive if you had Grub installed which you don't.  

> The only direction after that are how to boot from DVD or from a USB.  I  dont want to do that.  I want to partition the drive and install it on  half the drive.


You can't do that from windows, see above.  Your post isn't making sense to me.  It seems like you are trying to install by simply downloading it which won't work either.  Not really clear how you expect to get Ubuntu on the machine without using any of the standard methods.  Also, if you have windows 8 then you are dealing with UEFI/GPT partitioning so you might read a little about that as it adds some complexity to the old boot methods.

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

### Post by grahammechanical on 2014-10-03
If you have never installed Ubuntu on a windows 8 machine then you had best read this

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

This will help you understand partitioning.

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

What you will see when choosing the Something Else option

[http://askubuntu.com/questions/148881/dual-boot-windows-xp-and-ubuntu-12-04](http://askubuntu.com/questions/148881/dual-boot-windows-xp-and-ubuntu-12-04)

This is what you should expect to see once you have used the Something Else option to tell the installer the partitions to install Ubuntu in.

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

Regards.

---

