---
title: "Alternate text install do not let me install GRUB to a location other than MBR"
date: 2006-08-21
forum: Installation &amp; Upgrades
---

### Post by city-17 on 2006-08-21
Hi, i wish to install a 64 bit Ubuntu 6.06 DapperDrake in a third sata hd, all the disk for Ubuntu (the other two are configured in a RAID wich contains windows), my bios allows to boot it but i have trouble installing GRUB in it's MBR since the so called alternate installation installs GRUB in the MBR of the first disk and never asks a thing, having already screwed up the dell-mbr that allowed access to the partition wich contained dell utilities and needless to say that it doesn't boot neither Ubuntu nor windows, showing error 21. I'm not interested in how to dual boot the systems, i'm only interested in how to install grub or lilo in the MBR of my third sata.

At the installation process, after manually partitioning the disk, Ubuntu proceeds to install the packages and that's it, ejects cd and ask me to reboot to my new installed system, the installation process never asked me where i wanted to install GRUB and by default installs it in the first hd's MBR. However, i discovered that if i choose "back" instead of rebooting my system at the final stage of installation i gain access to a tree of the installation process where i can choose "install grub in a disk" and "install lilo in a disk". The first choice is the samo (same old s...) as before and the second one do let me install lilo in /dev/hdc but it crashes at 50% of the process, i mean a total stop.

This is what i've tried in livecd:

ubuntu@ubuntu:~$ sudo -s
root@ubuntu:~# mount /dev/sdc /media
mount: /dev/sdc already mounted or /media busy
root@ubuntu:~# grub-install --root-directory=/media/boot /dev/sdc
mkdir: cannot create directory `/media/boot/boot': No such file or directory

I also have investigated something about sudo apt-get install lilo and sudo apt-get install mbr but i don't give it a try since no hd's MBR is especified and may be samo.

Please help this newbie.](*,) 

Maybe helps telling you that my first attempt to install Ubuntu was from livecd and could be that the text installation detects something that changes its behavior. 
Thenks.
Please ask me if you don't understand something because English is not my native language.

---

### Post by confused57 on 2006-08-21
Here's a "howto" for installing grub using the desktop live cd:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

See the reply by 5-HT for selecting a different hard drive & partition to install grub.

---

### Post by city-17 on 2006-08-21
Thanks man, your reply was fast but i'm still having trouble:

grub> setup (sdc)
setup (sdc)

Error 23: Error while parsing number

There must be a way of setting up GRUB or LILO from installation because i have seen installation guides with screen captures that shows that step. 

Thanks anyway.

---

### Post by confused57 on 2006-08-22
> **city-17 said:**
> Thanks man, your reply was fast but i'm still having trouble:

grub> setup (sdc)
setup (sdc)

Error 23: Error while parsing number

There must be a way of setting up GRUB or LILO from installation because i have seen installation guides with screen captures that shows that step. 

Thanks anyway.

You might want bootup with the live cd, then open a terminal(Applications---Accessories---Terminal), enter:
```
sudo fdisk -l
```
The -l is a small "L"
This will show how Ubuntu recognizes your drives.

Grub uses a different way of naming harddrives and partitions than fstab or what you'll see with the above command.

hd0  =   sda    =     hda
hd1  =   sdb    =     hdb
hd2  =   sdc    =     hdc

The first column is how grub names hard drives.

hd0,0  =  sda1   =    hda1
hd0,1  =  sda2   =    hda2
hd0,2  =  sda3   =    hda3

This will give you an idea of how to specify where to install grub, using the live cd.

---

### Post by city-17 on 2006-08-22
I tried but i'm still in trouble:
 Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       18966   152344363+  83  Linux
/dev/sdc2           18967       19457     3943957+  82  Linux swap / Solaris

grub> setup (hd2)
setup (hd2)

Error 12: Invalid device requested
grub> setup (hd2,0)
setup (hd2,0)

Error 12: Invalid device requested
grub> setup (sdc,1)
setup (sdc,1)

Error 23: Error while parsing number

Could you install GRUB from the alternate text installer?

---

### Post by confused57 on 2006-08-22
Here's an excellent grub tutorial:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

This thread "may" help:
[http://www.ubuntuforums.org/showthread.php?t=239851](http://www.ubuntuforums.org/showthread.php?t=239851)
or
[http://www.ubuntuforums.org/showthread.php?t=234281](http://www.ubuntuforums.org/showthread.php?t=234281)

---

### Post by randell6564 on 2006-08-22
This link [http://linuxmafia.com/faq/Hardware/sata.html](http://linuxmafia.com/faq/Hardware/sata.html) will explain why you are having trouble.

S-ATA Raid devices are not compatible with Linux as of yet.

---

### Post by city-17 on 2006-08-29
I finally got ubuntu running, but at a high cost. I had to reconfigure the Raid array at id1 and id2 and leave the first disk alone for ubuntu at id0. Alternate text install can't detect windows on a sata raid configuration and that's why GRUB always get installed in the MBR of the first disk without asking. 

Thanks for the replies anyway.

---

