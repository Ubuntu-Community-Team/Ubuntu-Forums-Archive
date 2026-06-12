---
title: "question about upgrade from xubuntu 12.04 to xubuntu 14.04"
date: 2015-07-04
forum: Installation &amp; Upgrades
---

### Post by sam_baker2 on 2015-07-04
hi,
Soon, I will be upgrading from what I am using now,  Xubuntu 12.04 
( that does not have anything concerning Ubuntu 12.04 on it.) to
Xubuntu 14.04

When I run the update manager, and hit the upgrade to 14.04 button, a 
window pops up and says:
 "Welcome to Ubuntu 14.04 'Trusty Tahr"

I don't want Ubuntu 14.04 , I only want Xubuntu 14.04

If I hit the upgrade button, and I only have Xubuntu on
my machine, will I only get Xubuntu stuff, or will some
Ubuntu stuff be installed also.

Thanks for any info.

---

### Post by PaulW2U on 2015-07-04
Hi sam_baker2

As long as you've never installed the ubuntu-desktop package then you should upgrade to Xubuntu 14.04. Packages that are common to all the Ubuntu flavours will probably identify as being Ubuntu. If you want to be sure then type the following commands into a terminal or check in synaptic if you have it installed.

```
apt-cache policy ubuntu-desktop
```
```
apt-cache policy xubuntu-desktop
```
The output will tell you if either is installed.

For your upgrade to work correctly make sure you have xubuntu-desktop installed as the upgrade process will need to know what new packages may be required and what redundant packages should be deleted.

---

### Post by sam_baker2 on 2015-07-04
Thanks for reply PaulW2U

here is apt-cache policy ubuntu-desktop:
```

ubuntu-desktop:
  Installed: (none)
  Candidate: 1.267.1
  Version table:
     1.267.1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main amd64 Packages
     1.267 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/main amd64 Packages

```

here is apt-cache policy xubuntu-desktop:
```

xubuntu-desktop:
  Installed: (none)
  Candidate: 2.152+ppa2
  Version table:
     2.152+ppa2 0
        500 http://ppa.launchpad.net/xubuntu-dev/xfce-4.10/ubuntu/ precise/main amd64 Packages
     2.152 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/universe amd64 Packages

```

~Also, I use xfce desktop if that makes any difference

---

### Post by Bucky Ball on 2015-07-04
> **sam_baker2 said:**
> hi,
Soon, I will be upgrading from what I am using now,  Xubuntu 12.04 
( that does not have anything concerning Ubuntu 12.04 on it.)


Except for one major thing they share: the Ubuntu kernel.

> **sam_baker2 said:**
> 
If I hit the upgrade button, and I only have Xubuntu on
my machine, will I only get Xubuntu stuff ...



Yes. Whatever you have installed will be upgraded. Nothing will be added from any other flavour that is not already there. 

Bear in mind that, regardless of the Ubuntu flavour you are using, they all share one thing in common: the Ubuntu base kernel. Any flavour, or spin really, is the Ubuntu kernel plus whatever defaults the flavour or spin happens to add to it. That is the difference. 

Good luck with the upgrade. To add to what PaulW2U suggests, update and switch off any PPAs you've added manually prior to commencing.

---

### Post by sam_baker2 on 2015-07-04
Thanks Bucky Ball    My kernel is :  ```
 3.2.0-86-generic 
```   I have added PPA's manually, but I don't know how to turn them off before upgrading

---

### Post by Bucky Ball on 2015-07-04
Easiest way is to open 'Software and Updates'> Other Software> disable the third-party PPAs you've installed manually by unticking them. :)

You can also open a terminal, issue:

```
sudo nano /etc/apt/sources.list
```

and put a # in front of the PPAs you want to disable. You basically want the install as 'vanilla' as possible prior to the upgrade. Most upgrade problems, if not the majority, happen because of mismatched PPAs after the upgrade or a driver that is made redundant by the upgrade. 

Good luck and let us know of any issues.

---

### Post by sam_baker2 on 2015-07-04
Thanks again. Will do.

---

### Post by sam_baker2 on 2015-07-10
Installation of 14.04 went fine. ( was installed on a desktop AMD 64 )
I was surprised that google-earth worked, and that I was able to view the pictures that you can view 
when you zoom in. The install kept the original GE version.
 I installed xubuntu on a laptop earlier ( Intel 64 ), and for some reason
google-earth was removed , and upon downloading and installing the new google-earth, the little pictures
would not display.

   On the just done desktop installation, I kept all of the old libraries and I kept all of the original
settings that the install asked me if I wanted to exchange for new.
 I use xubuntu xfce, and I had to install new xfce 4.12 desktop

Generally everything went smooth except when I did a sudo apt-get update
I had to get a key from keyserver.ubuntu.com.
Now, when I do a 
```

sudo apt-get update

```
I get these:
```

Ign http://us.archive.ubuntu.com trusty InRelease
Ign http://us.archive.ubuntu.com trusty-updates InRelease
Ign http://us.archive.ubuntu.com trusty-backports InRelease
Ign http://extras.ubuntu.com trusty InRelease
Ign http://security.ubuntu.com trusty-security InRelease
Ign http://ppa.launchpad.net trusty InRelease
Ign http://deb.opera.com stable/non-free Translation-en_US
Ign http://deb.opera.com stable/non-free Translation-en
Ign http://extras.ubuntu.com trusty/main Translation-en_US
Ign http://extras.ubuntu.com trusty/main Translation-en
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US

```

Are these anything to worry about?

Everything said, was definitely easier than new LTS versions that I have
installed in the past, where I did a complete new install, off of the ISO

---

