---
title: "Installing Ubuntu without GRUB"
date: 2006-10-02
forum: Installation &amp; Upgrades
---

### Post by darckasasin on 2006-10-02
Hi, I have used Ubuntu in the past I think it works great, even better now that I found out about VMware. I have installed it with great ease, but I want to multi-boot it with Fedora Core and VectorLinux, but with a different boot loader in mind. Is there anyway I can opt-out of installing GRUB when installing so I have a clean MBR on the virtual HD?

---

### Post by orb9220 on 2006-10-02
Use alternate Iso is text based installer and gives more options on grub. [http://www.ubuntuforums.org/showthread.php?t=233444](http://www.ubuntuforums.org/showthread.php?t=233444)

---

### Post by darckasasin on 2006-12-15
uggghh, sorry for the bump, but I've just been inactive for a while. I've got a few new questions, but still related with grub. One thing I realized is that only desktop disc installs the desktop interface ](*,) 
before i get to that, i've changed my mind about opting out of the grub installation. Is there anyway I will be able to install grub onto a floppy during the ubuntu *desktop* installation?

---

### Post by bulldog on 2006-12-15
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

Take a look here if you can find something you like.

---

### Post by darckasasin on 2006-12-15
That first one looks promising. I'll have to to try that tomorrow. Can't now because I haven't installed ubuntu just yet.

---

### Post by confused57 on 2006-12-15
The alternate cd installer allows you to select where to install grub, the desktop live cd automatically installs grub to the mbr:

[http://www.ubuntuforums.org/showthread.php?t=188819](http://www.ubuntuforums.org/showthread.php?t=188819)

See the homepage of the first link bulldog gave you for installing with the alternate cd:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by darckasasin on 2006-12-15
I keep on seeing all this about an alt installer! wheredo you get the alt. cd installer?! I don't know if you realize, but I'm an absolute Ubuntu n00b, so I have no idea where anything is.

---

### Post by confused57 on 2006-12-16
> **darckasasin said:**
> I keep on seeing all this about an alt installer! how do you get to the alt. installer?! I don't know if you realize, but I'm an absolute Ubuntu n00b, so I have no idea where anything is.
Go to the Ubuntulinux homepage, click on downloads:
[http://www.ubuntu.com/](http://www.ubuntu.com/)

select a mirror close to you, click on other installation options, then you should get download options similar to this(including the alternate cd iso):
[http://ubuntu.cs.utah.edu/releases/edgy/](http://ubuntu.cs.utah.edu/releases/edgy/)

---

### Post by Herman on 2006-12-16
Hello darckasasin,
It looks like I'm the last one here. :D
bulldog and confused57 are right. If you use the 'Alternate' CD to install Ubuntu, you can perform the installation up until you get to this step, which is close to the end of the installation.

[CENTER][IMG]http://users.bigpond.net.au/hermanzone/p2d/21fat32.png[/IMG]
[/CENTER]
 
           If you choose <No> (not to install to MBR), you will be given an opportunity to specify somewhere else instead...

[CENTER]...now Click this link>[GO]("http://users.bigpond.net.au/hermanzone/p6.htm#If_you_choose_No__to_Install_GRUBs_IPL_to_a_custom_location")
[/CENTER]

Of course you would have a blank, formatted floppy disk ready before you begin the installation.
That link will explain to you how to install Grub to a floppy disk during the installation of Ubuntu if you use the 'Alternate' CD. If anything goes wrong, such as the floppy disk turns out to be a 'dud' as can happen with floppy disks, you can use a [Super Grub Disk]("http://supergrub.forjamari.linex.org/") to boot Ubuntu with rather than have to re-install.
The 'Alternate' CD will install the same operating system (complete with a desktop), as the 'Desktop' CD. It just features more options so some people think it's confusing.

Otherwise, If you use the 'Desktop' CD, you can install Grub to MBR, but if it's your Windows MBR you are worried about, you see how to make a backup of it and restore it again afterwards with the 'Desktop CD' this way, MBR backup and restore.............................................................[GO]("http://users.bigpond.net.au/hermanzone/p13.htm#mbr_dd")
You can make a grub floppy disk manually this way,
How to make your own personalized Grub Floppy Disk........................................ [GO]("http://users.bigpond.net.au/hermanzone/p15.htm#grub_floppy_howto_make")

Actually, there is nothing wrong with installing Grub to MBR, but do as you please. 
> I keep on seeing all this about an alt installer! how do you get to the alt. installer?! I don't know if you realize, but I'm an absolute Ubuntu n00b, so I have no idea where anything is. That depends on your location (what mirror you use), but the 'Alternate' CD can normally be found somewhere nearby on the same sites where the 'Desktop' CDs are found. [Download]("http://www.ubuntu.com/download")

Regards, Herman :D

Oh, he-he, confused57 beat me to it. :D

---

### Post by darckasasin on 2006-12-16
oh, good. thanks for your help guys. i'll see what I can do. I'm up anyways (already 1AM over here!)


EDIT: Sorry i couldn't get back sooner, but it works! Thanks for all your help, guys!

---

### Post by 5thgendriver on 2007-03-22
ok so i know this is an old post but i think i have a solution to this issue because i have a similar issue

so i spend alot of time setting things up the way i want and i run 3 operating systems it isnt easy to configure vista - media center 2005 - and ubuntu to work together in perfect  harmony - i hosed my ubuntu installng beryl and now i want to just reinstall ubuntu and not grub - currently i have a dump of my bootloader in my windows directory and the boot.ini file has an entry directed to it so i can boot ubuntu - so i gave it some thought and boom i decided attach another hdd and install grub to it then remove it -- works!!! pretty F***ing easy

---

