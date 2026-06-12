---
title: "No GUI after Lubuntu install, P4 256 mb ram"
date: 2014-03-30
forum: Installation &amp; Upgrades
---

### Post by marshal-banana on 2014-03-30
hi, trying to install lubuntu desktop on " P4 256 mb ram" , installed ubuntu 12.04 minimal, then installed  lubuntu desktop via sudo apt-get install lubuntu-desktop, after rebooting there's no GUI, how to fix this,,, thx

---

### Post by Rex Bouwense on 2014-03-30
> **marshal-banana said:**
> hi, trying to install lubuntu desktop on " P4 256 mb ram" , installed ubuntu 12.04 minimal, then installed  lubuntu desktop via sudo apt-get install lubuntu-desktop, after rebooting there's no GUI, how to fix this,,, thx
Did you follow the instructions given in this site?
[https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall)
While Ubuntu 12.04 is still supported, the Lubuntu 12.04 has reached its EOL.  That means you will not get security updates and patches for that part of your system.  You do have enough RAM to install the latest Lubuntu (13.10) if that is what you want.

---

### Post by sudodus on 2014-03-31
*Edit*: **[SIZE=4]General tips for old hardware[/SIZE]**

Please see this link [Old hardware brought back to life]("http://ubuntuforums.org/showthread.php?t=2130640")

**[SIZE=4]Graphics card[/SIZE]**

If you have problems with the graphics, please tell us about your graphics chip/card

- Brand name and model
[SIZE=4][B]
Ubuntu mini.iso[/B][/SIZE]

I suggest that you try ***Lubuntu Core*** 13.10 or Trusty.

Lubuntu Core is one of the alternatives to be installed from the Ubuntu mini.iso and it is lighter than standard Lubuntu. And I think that is important, since 256 MB RAM is very low.

The version 13.10 is the only version that is supported for Lubuntu. The next version, Trusty, to become 14.04 LTS, is at the beta 2 stage, and if you are prepared to have some problems with the daily upgrades, you can try it now, or wait a few more weeks until it is released.
[B][SIZE=4]
Alternative installers[/SIZE][/B]

**[SIZE=2]The One Button Installer can install systems with 128 MB RAM[/SIZE]**

 The One Button Installer can install dual boot systems. 
Lubuntu  13.10 'Saucy' can be installed with the One Button Installer in Pentium  M and Celeron M computers using fake-PAE. (Lubuntu 14.04 LTS 'Trusty'  can use the boot option **forcepae** and can be installed using the standard installers.) 
[https://help.ubuntu.com/community/OBI](https://help.ubuntu.com/community/OBI) 
 
[B][SIZE=2]The 9w installer can install systems with 80 MB RAM
[/SIZE][/B]
 The 9w installer can install systems with 80 MB RAM, but **Lubuntu Core Trusty** needs 128 MB RAM to run and at least 256 MB RAM to be really useful. 
[http://phillw.net/isos/linux-tools/9w/](http://phillw.net/isos/linux-tools/9w/) 
Computers  with less memory than 256 MB of RAM can be used in text mode (or maybe  in graphics mode with some other really small linux distro). 
See posts #88, 89 and the following posts in this thread about 9w. 
[http://ubuntuforums.org/showthread.php?t=2209683&page=5&p=12957586#post12957586](http://ubuntuforums.org/showthread.php?t=2209683&page=5&p=12957586#post12957586) 
[http://ubuntuforums.org/showthread.php?t=2209683&page=6&p=12957950#post12957950](http://ubuntuforums.org/showthread.php?t=2209683&page=6&p=12957950#post12957950) 
[http://ubuntuforums.org/showthread.php?t=2209683&page=8&p=12962755#post12962755](http://ubuntuforums.org/showthread.php?t=2209683&page=8&p=12962755#post12962755)

---

### Post by marshal-banana on 2014-04-01
hi, installed Lubuntu 13.10  via lubuntu 13.10 alternate with unetbootin, and all I got, is command line ( enter login & password ) ,, no desktop, why??

---

### Post by sudodus on 2014-04-01
I think the installation was successful from the alternate installer. Maybe you have problems with the graphics chip/card.

1. Please describe your computer! It makes it possible to give relevant advice to solve your particular problem. Otherwise we can only guess.

- Computer brand name and model
- CPU (you told us P4), what speed or clock frequency (MHz)
- (You told us RAM size 256 MB)
- *Graphics chip/card brand name and model*

2. You can try some boot option. Start with ***nomodeset*** according to the following link. You can also try the other boot options available at F6.

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by marshal-banana on 2014-04-01
I have : 
Intel D865GBF board
P4 2.8 Ghz processor
256 mb DDR 333 RAM, 16 mb goes to the graphic card so 240 i think
graphic card: built in Intel extreme graphics 2
80 gb HDD

I have this machine since 2004

---

### Post by sudodus on 2014-04-01
> **marshal-banana said:**
> I have : 
Intel D865GBF board
P4 2.8 Ghz processor
256 mb DDR 333 RAM, 16 mb goes to the graphic card so 240 i think
graphic card: built in Intel extreme graphics 2
80 gb HDD

I have this machine since 2004

Good, I think there is a solution :-)
The CPU is definitely powerful enough. The RAM is really low, too low for 'modern browsing habits'. The graphics might cause a problem that can be solved.

> **sudodus said:**
> *Edit*: **[SIZE=4]General tips for old hardware[/SIZE]**

Please see this link [Old hardware brought back to life]("http://ubuntuforums.org/showthread.php?t=2130640")
...

Please try the tip from the link above for Intel graphics from the 8xx family: Create an **/etc/X11/xorg.conf** file with the following contents:

```
Section "Device"
    Identifier "Intel Graphics"
    Driver "intel"
    Option "AccelMethod" "uxa"
EndSection

```

There's a tab in front of the three middle lines (one tab but no spaces, you have to make it like that to work).

-o-

If the solution above with UXA acceleration does not help, I suggest that you try a system based on Ubuntu 12.04 LTS. Maybe the alternate installer works, but it is close to the limit, because it might need more RAM than you have. (The installer for Lubuntu 13.10 needs less RAM because it uses zRAM technology.) But it is possible to use the ***One Button Installer ***according to the following link.
[URL="http://ubuntuforums.org/showthread.php?t=2172971"]
One Button Installer, 'OBI'[/URL]

You can try to install either of ***Bento, Bodhi, LXLE ***or*** Precise Gnome Classic Tweaks*** from a tarball, but expect rather poor performance of the installed system with only 256 MB RAM.

Another alternative is to install ***some other and  really light-weight linux distro, ***or even better,*** try to find more RAM of the same kind.***

---

### Post by marshal-banana on 2014-04-02
thank you, I tried but didn't work,, i've installed puppy linux

---

### Post by sudodus on 2014-04-02
I'm glad you found a linux distro that works well for you :-)

***Puppy*** is one of those really light-weight good alternatives.

---

