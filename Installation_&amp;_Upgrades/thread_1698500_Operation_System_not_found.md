---
title: "Operation System not found"
date: 2011-03-02
forum: Installation &amp; Upgrades
---

### Post by Alex2006 on 2011-03-02
Hello
I'm new of Linux. I tried to install the Xubuntu-alternate-10.10-i386 on an old HP Omnibook 4150.(Pentiun II, 128 MB RAM, Windows 98).
I followed the specific information provided in the following guide.
[http://wiki.ubuntu-it.org/Installazione/Generale](http://wiki.ubuntu-it.org/Installazione/Generale)
I wanted to create a single partition just for Ubuntu becuse I do not need Windows anymore.
The installation apparently was ok, without problem until the end.
When it asked me to reboot, I did it and by intervening in the BIOS to boot from Harddisk.
After the first screen with the HP logo appeared a black page with the words
Operating system not found_ and blinking cursor.
At the press of sending the message is repeated.
Can you help me to undertsand the problem and how to solve it ?
I cannot open comand line because it is looked and all is black
 
Thanks very much

---

### Post by Kirboosy on 2011-03-02
Welcome to the Forums! :D

Sounds like your BIOS isn't even detecting a Operating System. I would try reinstalling it. 

Also another light version of ubuntu is [lubuntu]("http://%22http://www.lubuntu.net")

---

### Post by Hakunka-Matata on 2011-03-02
> Get Xubuntu
Xubuntu releases:

    * 10.10, codename Maverick Meerkat (Latest stable release).
    * 10.04, codename Lucid Lynx, includes Long Term Support.

Minimum system requirements

You need 192 MB RAM to run the Live CD or 192 MB RAM to install. The Alternate Install CD only requires you to have 64 MB RAM at install time.

To install Xubuntu, you need 2.0 GB of free space on your hard disk.

Once installed, Xubuntu can run with starting from 192 (or even just 128) MB RAM, but it is strongly recommended to have at least 256 MB RAM.

RAM may be a problem

---

### Post by sanderj on 2011-03-02
> **Alex2006 said:**
> Hello
I'm new of Linux. I tried to install the Xubuntu-alternate-10.10-i386 on an old HP Omnibook 4150.(Pentiun II, 128 MB RAM, Windows 98).


Don't bother: your RAM is below the *minimum* system requirements.

[http://www.xubuntu.org/getubuntu](http://www.xubuntu.org/getubuntu) :


> 
Minimum system requirements
You need 192 MB RAM to run the Live CD or 192 MB RAM to install. The Alternate Install CD only requires you to have 64 MB RAM at install time.

To install Xubuntu, you need 2.0 GB of free space on your hard disk.

Once installed, Xubuntu can run with starting from 192 (or even just 128) MB RAM, but it is strongly recommended to have at least 256 MB RAM.


---

### Post by Vi3tHoneyX on 2011-03-02
[COLOR=DarkRed]You could also try install [Crunchbang]("http://crunchbanglinux.org/")

Hopefully you have more luck with it. :)[/COLOR]

---

### Post by Hakunka-Matata on 2011-03-02
[http://www.puppylinux.com/]("http://www.puppylinux.com/")

Another great distro for old hardware

---

### Post by Alex2006 on 2011-03-02
Thanks to everyboby.
I'll try with an other distro an I'll tell you

---

### Post by Alex2006 on 2011-03-04
Hello
Xubuntu now is working well. I swiched off and switched on againd and it worked well.
 
BUT TOO SLOWLY!!!
 
So I would like to install PUPPY LINUX. I have Puppy Linux 431, but I can't boot it from CD. (setting bios for start from CD)
How can I do?
Do I need to erase Xubuntu? or to Format Hard disk before installing Puppy?
Why the boot from CD deosn't work?
 
Thanks

---

### Post by Hakunka-Matata on 2011-03-04
Puppy 4.3.1. is a good place to start.  Does your BIOS not allow you to boot from CD?

Burn Puppy .iso to USB is another option, can your computer Boot from USB?
 
[http://unetbootin.sourceforge.net/]("http://unetbootin.sourceforge.net/")

---

### Post by Alex2006 on 2011-03-04
No  my BIOS has, as first option, Boot from CD but when I switch on xubuntu starts.
Yes my PC has USB port but when I used it with Windows 98, it wasn't able to see any USB key.
 Can I use USB port? How?
Thanks

---

### Post by Alex2006 on 2011-03-04
My Bios says it's possible to boot from an external device!

---

### Post by Hakunka-Matata on 2011-03-04
PuppyLinux installation works the same way Ubuntu installation works.  You have to download the PuppyLinux ISO file, and burn it to either CD, or USBFlash drive.  Then boot your computer with the CD or the USBFlash drive.  You can use the unetbootin site and program to make your bootable USBFlash drive.

---

### Post by cgroza on 2011-03-04
Are you sure you burned Puppy as an iso file and at the lowest speed?

---

### Post by Alex2006 on 2011-03-08
I burned Puppy linux 2.16 and now all is ok. It works very well with Hp Omnibook 4150. Thanks

---

