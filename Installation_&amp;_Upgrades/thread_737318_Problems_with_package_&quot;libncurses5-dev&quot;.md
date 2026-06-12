---
title: "Problems with package &quot;libncurses5-dev&quot;"
date: 2008-03-27
forum: Installation &amp; Upgrades
---

### Post by lokiti on 2008-03-27
I installed Gusty Ubuntu. But the sound system not work.
I try to install : Alsa-driver , Alsa-lib, Alsa-Utils
But when i do 
> 
cd ../alsa-utils*
sudo ./configure

it has a problems
> configure: error: this packages requires a curses library

and i downloaded file "libncurses5-dev_5.6+20070716-1ubuntu3_i386"
but I dont know how to use it . Plz help me....It's the first time I use Linux, so I have no experience.......

---

### Post by wolfen69 on 2008-03-27
look in synaptic for libncurses5.

---

### Post by Dean Powell on 2008-03-27
Hi:

You need to install the ncruses development library.  There are a couple of ways to do this.  An easy one is to open a terminal session, then from the command line:

sudo apt-get install libncurses5-dev

This will automatically download and install the correct package for you.

Hope this helps.

Regards,
Dean

---

### Post by lokiti on 2008-03-28
I tried
> sudo apt-get install libncurses5-dev

But still hav error
l> lokiti@lokiti-desktop:~$ sudo apt-get install libncurses5-dev
[sudo] password for lokiti:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[COLOR="Red"]E: Couldn't find package libncurses5-dev[/COLOR]


What should I do ? Plz help me

---

### Post by buntu_Geek on 2008-03-28
While doing the configure step for your source package( that you desire to..)

Do this...

sudo apt-get build-dep <package you are trying to install>

This will tell what are the dependencies to install and automatically downloads and installs the dependencies... ( easy as that...)

---

