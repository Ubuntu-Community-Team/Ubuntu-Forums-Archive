---
title: "well this sucks"
date: 2007-07-20
forum: Installation &amp; Upgrades
---

### Post by jlayer21 on 2007-07-20
ok ive got the iso image but my dvd drive is going out in my laptop is there a way to install without a cd? ive got the iso image on my ext drive but it wont boot (thought id try it)  anybody got any ideas im running out im losing control of my comp AHHHHHHHHH!!!!!

---

### Post by overdrank on 2007-07-20
> **jlayer21 said:**
> ok ive got the iso image but my dvd drive is going out in my laptop is there a way to install without a cd? ive got the iso image on my ext drive but it wont boot (thought id try it)  anybody got any ideas im running out im losing control of my comp AHHHHHHHHH!!!!!



HI maybe this link will help
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

Also you can look at this link 
[http://wubi-installer.org/](http://wubi-installer.org/)
Hope this helps! Good luck!

---

### Post by jlayer21 on 2007-07-20
ok so looking around i find grub what is this im a total newb i know linux is open source and can be modified and easily upkept but what do i NEED to know what do i need to do still tryin to install :(

---

### Post by overdrank on 2007-07-20
> **jlayer21 said:**
> ok so looking around i find grub what is this im a total newb i know linux is open source and can be modified and easily upkept but what do i NEED to know what do i need to do still tryin to install :(

Hi that is why I posted those links because the first link has info on installing without a cd drive.

Installation without a CD

The documents listed below provide instructions for installing Ubuntu without using a CD or CD-ROM drive.

    *

      SmartBootManagerHowto - Installing from a PC which will not boot from CD
    *

      Installation/FromUSBStick - Installing from a USB memory stick
    *

      Installation/WithFloppies - Installing without a CD drive over a network
    *

      Installation/FromHardDriveWithFloppies - Installing without a CD drive or network capabilities from a hard drive
    *

      Installation/FromWindows - Installing from Windows without using floppies, a CD, or any other removable media
    *

      Installation/FromLinux - Installing from an existing Linux system without any removable media

---

### Post by EndPerform on 2007-07-20
> **jlayer21 said:**
> ok so looking around i find grub what is this im a total newb i know linux is open source and can be modified and easily upkept but what do i NEED to know what do i need to do still tryin to install :(

Have you checked any of the links on the wiki page previously posted?  One of those options should work for you.  It's tough when your machine does not have a working CD/DVD drive, but if you have access to a machine with a working drive, you should be able to install using one of the alternative methods.  This one sticks out as a possibility: [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by Gremlinzzz on 2007-07-20
maybe you can burn a small file 
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by jlayer21 on 2007-07-21
i appreciate everyones help i finally got it installed with the 2nd link in the first post. however now im getting an error 17 is this because im trying to dual boot and if so what do i have to do to change it

---

### Post by overdrank on 2007-07-21
> **jlayer21 said:**
> i appreciate everyones help i finally got it installed with the 2nd link in the first post. however now im getting an error 17 is this because im trying to dual boot and if so what do i have to do to change it

Ok you used the second link in my post which is wubi and now you get a grub error 17?:(

---

### Post by jlayer21 on 2007-07-21
yeah im gettin the eroor even though checksums came out ok it says that root file menu list is missing i think?

---

### Post by overdrank on 2007-07-21
> **jlayer21 said:**
> yeah im gettin the eroor even though checksums came out ok it says that root file menu list is missing i think?

Ok first off I am sorry I have never used wubi to install before so I will need to do that before I recommend again. Apparently error 17 is that grub cannot find ubuntu. So I suggest you you look at the FAQ on this page
[http://wubi-installer.org/faq.php#use](http://wubi-installer.org/faq.php#use)
And if all else fails uninstall via wubi directions and try again because the download coul have been corrupted or try one of the other ways suggested in the first link. You can try to reinstall the grub by super grub also it can be used by floppy, usb drive or cd. Again I am sorry I could not be of more help. Good luck!:(

---

### Post by jlayer21 on 2007-07-22
> **overdrank said:**
> Ok first off I am sorry I have never used wubi to install before so I will need to do that before I recommend again. Apparently error 17 is that grub cannot find ubuntu. So I suggest you you look at the FAQ on this page
[http://wubi-installer.org/faq.php#use](http://wubi-installer.org/faq.php#use)
And if all else fails uninstall via wubi directions and try again because the download coul have been corrupted or try one of the other ways suggested in the first link. You can try to reinstall the grub by super grub also it can be used by floppy, usb drive or cd. Again I am sorry I could not be of more help. Good luck!:(

okay heres the lowdown. i got ubuntu installed onto my external hard drive on its own partition.  it goes to the dual boot screen and then of course does not load ubuntu for whatever reason its giving me error 17.  now when it was done downloading it did checksums and said it was good so it should have been a complete and usable download right?  is it maybe somoe settings i need to change to allow it to dual boot?  maybe there is another explanation.

---

